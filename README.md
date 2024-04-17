This is my Project on Terraform with AWS 
I will clearly demonstrate all the steps I followed along with the solutions I came across for the challenges I faced while working on this Project.
This is a project to host a static website on S3 bucket in AWS.
Pre-requisites Required:
1. Terraform Installed
2. AWS Account

Step1:
Create the required folders in your local for writing the code and refer to the HashiCorp-official documentation for adding providers section.
Create a new providers.tf file and add the required piece of code from the terraform docs and then run it using terraform init. Then a Terraform lock file will be created.
Now create main.tf, variables.tf and run the Terraform commands.

Note: If the AWS account is not linked with the Terraform, it throws an error here, so first link it.

After successful execution, an S3 bucket would be created with our given name but we need to make it's access to public and staic website hosting should be on.

Note: Here, I have faced an issue as my bucket failed to create. So for that I have done some steps in my AWS account. First I have created an IAM user with an access key, then
I have attached IAM S3 bucket policies on it.

Steps to perform in AWS:

Log in to the AWS Management Console
Go to the IAM dashboard.
Create an IAM User:

Click on "Users" in the left navigation pane.
Click on the "Add user" button.
Enter a username for the new IAM user.
Select "Programmatic access" as the access type.
Click on "Next: Permissions".
Set Permissions:

Choose whether to add the user to an existing group with the necessary permissions or attach policies directly to the user.
Select the policies that grant the required permissions for the Terraform operations you intend to perform.
Click on "Next: Tags" if you need to add tags, otherwise proceed to review.
Review and Create:

Review the user's configuration to ensure it has the correct permissions.
Click on "Create user".
Access Key Creation:

Once the user is created, you'll be prompted to view and download the user's access keys.
Click on "Download .csv" to save the access key ID and secret access key to a secure location on your system.
Configure AWS Credentials:

Install the AWS CLI if you haven't already.
Run aws configure in the terminal.
Enter the access key ID and secret access key when prompted.
Specify the default region and output format as per your preference.
Verify Credentials:

After configuring the AWS CLI, you can verify that the credentials are correctly set up by running aws sts get-caller-identity in the terminal.
If the command returns information about the IAM user you created, it means the credentials are correctly configured and you're authenticated with AWS.
By following these steps, you'll have set up AWS credentials for an IAM user with limited permissions, which is a more secure approach than using root user access keys.

Step2: Now, add corresponding code into the main.tf file for editing the permissions of the s3 bucket with static hosting to be turned on.

Step3: Create index.html, error.html to write the webpage that we would like to host.

Now, run the Terraform apply command and we can see the objects inside our S3 bucket.

And in properties, we could see a link at static website hosting in Properties section.

That's the web link where our website is being hosted. 

After successful creation of everything, we can see a Statefile gets created that has all the infrastructure we defined. 


