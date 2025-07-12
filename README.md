# README: Hosting a Static Website on AWS S3

Welcome to the quick guide on how to host a static website on AWS S3 (Simple Storage Service). This guide will walk you through every step to set up your static site quickly and easily. 

## :rocket: Introduction

S3 (Simple Storage Service) lets you store files in the cloud—and one of its lesser-known superpowers is that it can serve websites too! It’s perfect for static websites (those made with just HTML, CSS, and JavaScript), and if you're on the AWS Free Tier, you can host up to 5GB of content for free for a whole year.

## :scroll: Step-by-Step Guide

Follow these steps to host your static website on AWS S3:

1. **Log into AWS**
   
   - Go to your AWS console and search for "S3" in the search bar, then select "S3" when it appears.

2. **Create a Bucket**

   - Click on "Create bucket."
   - Give your bucket a unique name (think of it like a folder name on the internet).
   - Choose your preferred region.

3. **Adjust Bucket Permissions**

   - Scroll to the Block Public Access section and uncheck “Block all public access”.
   - AWS will warn you about making the bucket public—confirm that this is what you want.

4. **Select Your Bucket**

   Once created, select your bucket from the list.

5. **Enable Static Website Hosting**

   - Go to the Properties tab in your bucket.
   - Scroll down to Static website hosting, click Edit, and turn it on.
   - Choose “Host a static website”, and specify your homepage file (usually index.html).

6. **(Optional) Set Up an Error Page**

   - You can also add an error.html file to display when someone lands on a broken or non-existent link.

7. **Upload Your Website Files**

    - Head over to the Objects tab.
    - Click Upload, then add your HTML, CSS, JS files (make sure your index.html is there!).

8. **Bucket Policy for File Access**

   - Create a bucket policy to enable access to the files.
   - Navigate to the "Permissions" tab and under the "Bucket policy" section, enter the provided policy, ensuring to change the Resource to your bucket's ARN followed by "/*".
    
    * **Note your bucket ARN**, and replace `your-bucket-name` below.

      **Bucket Policy:**
      
      ```json
      {
          "Version": "2012-10-17",
          "Statement": [
              {
                  "Sid": "PublicReadGetObject",
                  "Effect": "Allow",
                  "Principal": "*",
                  "Action": "s3:GetObject",
                  "Resource": "arn:aws:s3:::your-bucket-name/*"
              }
          ]
      }
      ```

9. **Final Configuration**

    - Navigate to the "Properties" tab and load the bucket's endpoint. The "index.html" file will serve as the home page.
    - In case of an error (e.g., the index file is not available), the "error.html" page will be returned at the endpoint.

## :page_with_curl: Sample Website Pages

The article includes sample website pages for your reference:

- **index.html**: A basic static web page with AWS S3-themed content.

## :tada: Conclusion

With these steps, you can easily host your static website on AWS S3, benefiting from its simplicity, speed, and cost-effectiveness. Have fun hosting your website!

