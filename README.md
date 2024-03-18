# AWS Password Manager

![Simpsons](/images/200w.gif)

![Office](/images/office.gif)


Password manager using Passbolt through AWS

## Table of Contents

- [Project Overview](#project-overview)
- [Tools Used](#tools-used)
- [Demo](#demo)

## Project Overview
- Leveraging AWS and Passbolt to successfully create a self-hosted password manager to store sensitive information (passwords) and manage them enforcing data protection.

- Implementing HTTPS encryption to safeguard sensitive data trasnsmitted to and from the password manager

- Configure and maintain the domain hosting for the password manager, ensuring accessibility and security.


## Tools Used

- AWS
- VirtualBox (Ubuntu)
- PassBolt
- Namecheap -(Domain)

## Demo

### Passbolt 
    - Get started with the Community version of Passbolt Pro.
    - Select AWS and then press Deploy to AWS
    - After subscribing, I proceeded with the default setup.
![Passbolt](/images/passboltconfig.png)

    - Setup a new security group to allow traffic for Passbolt
![PassboltSG](/images/passboltsg.png)
    - Created a new key pair and dragged file into my Ubuntu under PASSBOLT.pem on virtual machine desktop.
![PassboltKP](/images/passboltkp.png)
    - Successful launch of EC2 instance from Passbolt and in AWS. (Instance has to initialize and be checked)
![PassboltS](/images/passbolts.png)
![PassboltEC2](/images/awsec2running.png)

#### AWS
    - After EC2 has been initialized, I copied the public IPv4 address and opened in new tab of web browser. Caveat: entered http:// in front of the IPv4 address. Https is not configured yet.
![PassboltHTTP](/images/httppass.png)

### Connecting to EC2 Instance from Ubuntu VM

In the terminal of the Ubuntu machine, ensure to change the permissions so the key isn't publically viewable and then ssh into the ec2 isntance.
``` bash
            cd Desktop   
            chmod 400 "PASSBOLT.pem"
            ssh -i PASSBOLT.pem admin@[ec2ipv4 address]
```
![EC2Connect](/images/connected.png)

### Nginx Configuration
```bash
    sudo nano /etc/nginx/sites-enabled/nginx-passbolt.conf
```
Updated server name to my domain I purchased from namecheap.
![EC2Connect](/images/servername.png)

```bash
sudo dpkg-reconfigure passbolt-ce-server
```

### Passbolt Server Config

![PassConfig](/images/passconfig1.png)
![PassConfig2](/images/passconfig2.png)
![PassConfig3](/images/passconfig3.png)

- The next steps I entered in my domain site and admin for the domain site.

![PassConfi4](/images/domainsite.png)
![PassConfi5](/images/adminsite.png)

- When successful should display similar to below. If failed, ensure the correct domain site is entered in the nginx config.

![PassConfi6](/images/successcertificate.png)

- Navigate to the domain site and SSL access should be enabled
![SSLenabled](/images/SSLenabled.png)

After all the configuration has been completed in Passbolt, I downloaded the extensions and downloaded the passkit provided. It also presented me with a security token.

![Sectoken](/images/sectoken.png)

### Password Manager

Password manager has been successfully setup

![PassMan](/images/PasswordMan.png)

### Terminate Instance
![Term](/images/terminstance.png)

### Credits

Credits to Pavel Hrabec 





