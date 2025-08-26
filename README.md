# S3 File Storage API

**S3 File Storage API** is a backend service built with **Java** and **Spring Boot** that provides RESTful endpoints to upload, download, and delete files from an **AWS S3 bucket**. It is designed with profile-based configurations, allowing for easy setup in both local development environments and production deployments on AWS EC2.

## 🚀 Features

- **File Management**: Core functionalities to upload, download, and delete files.
- **Direct AWS S3 Integration**: Uses the AWS SDK for Java to communicate securely with S3.
- **Profile-Based Configuration**: Supports separate configurations for `local` (with access keys) and `dev` (using IAM roles) environments.
- **RESTful Endpoints**: Simple and intuitive API for easy integration with any client application.
- **Scalable Service**: Built on Spring Boot, making it robust and ready for production.

## 🛠️ Tech Stack

### Backend:
- Java
- Spring Boot
- Spring Web

### Cloud Services:
- AWS S3 (Simple Storage Service)
- AWS SDK for Java 2.x

## 📂 Project Structure
```
s3filestorage/
└── src/
    └── main/
        └── java/
            └── com/marvel/s3filestorage/
                ├── config/     # Spring Boot Configuration (S3 Client)
                ├── controller/ # API Controllers (Endpoints)
                └── service/    # Business Logic (S3 Operations)
```

## 📦 Installation & Setup

### 1️⃣ Clone the Repository
```sh
git clone [https://github.com/utkarshanand07/S3FileStorage.git](https://github.com/utkarshanand07/S3FileStorage.git)
cd S3FileStorage
```

### 2️⃣ Configure AWS S3
This project uses Spring Profiles to manage configurations.

#### For Local Development (`local` profile)
This profile uses static AWS credentials.
1.  In `src/main/resources/`, create an `application-local.properties` file.
2.  Add your AWS credentials and bucket details:
    ```properties
    cloud.aws.credentials.access-key=YOUR_AWS_ACCESS_KEY
    cloud.aws.credentials.secret-key=YOUR_AWS_SECRET_KEY
    cloud.aws.region.static=your-aws-region
    aws.bucket.name=your-s3-bucket-name
    ```
3.  Activate the profile by setting `spring.profiles.active=local` in the main `application.properties` file.

#### For Production/Deployment (`dev` profile)
This profile is designed for deployment on AWS (e.g., an EC2 instance) and uses an IAM role for credentials.
1.  Ensure the EC2 instance has an IAM role attached with permissions to access the target S3 bucket.
2.  In `src/main/resources/`, create an `application-dev.properties` file.
3.  Add your region and bucket details:
    ```properties
    cloud.aws.region.static=your-aws-region
    aws.bucket.name=your-s3-bucket-name
    ```
4.  Activate the profile by setting `spring.profiles.active=dev` before deployment.

### 3️⃣ Run the Application
You can run the application using the Maven wrapper:
```sh
# Make sure you have activated the desired profile
./mvnw spring-boot:run
```
The server will start on the default port (usually 8080).

## 📜 API Endpoints
| Method | Endpoint | Description |
|---|---|---|
| POST | `/upload` | Uploads a file. The file should be sent as multipart/form-data. |
| GET | `/download/{filename}` | Downloads the specified file from the S3 bucket. |
| DELETE | `/delete/{filename}` | Deletes the specified file from the S3 bucket. |

## 🚀 Deployment
1.  **Create an S3 Bucket** in your AWS account.
2.  **Create an IAM Role** with `S3FullAccess` (or more restricted) permissions and attach it to your EC2 instance.
3.  **Build the project** into a JAR file: `./mvnw clean package`.
4.  **Deploy the JAR file** to your configured EC2 instance and run it with the `dev` profile activated.

## 🐾 Connect With Us
- **Project Link:** [S3FileStorage on GitHub](https://github.com/utkarshanand07/S3FileStorage)
- **Author:** [Utkarsh Anand](https://github.com/utkarshanand07)

---

⭐ **If you like this project, consider giving it a star!** ⭐
