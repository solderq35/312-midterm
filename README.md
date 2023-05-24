# 312 Midterm Minecraft Server Setup Guide

References
- https://www.linkedin.com/pulse/setup-minecraft-server-java-edition-aws-ec2-keran-mckenzie/
- https://techviewleo.com/install-java-openjdk-on-amazon-linux-system/
- ChatGPT

## EC2 Setup

- From the AWS homepage / dashboard, type in `EC2` into the upper left search bar, and click on it to go to the EC2 menu.

- From the EC2 menu, click on the `Launch Instance` button.

- In the Launch Instance menu, name your EC2 instance something like "Minecraft" so you can remember it.

- For the `Application and OS Images (Amazon Machine Image)` menu, select an Amazon Linux, 64bit (x86) OS image. 
  - This should be the **default** option.

- For the `Instance type` menu, select t2.small (should pick a t2 small or bigger for this).

- For `Key pair (login)` menu, I recommend just creating a new SSH key (click the `Create new key pair` button). I used the default options (`RSA`, `.pem`). 
  - Name the keypair something memorable, like `MinecraftKey`. In my case though I'm reusing an old key called "lab7".

- In the `Network Settings` menu, click the `Edit` button to the right to edit the Network Settings. 
  - Set `Auto-assign public IP` to `Enable`, if not already the case
  - Click on "Create Security Group"
  - Keep the existing default SSH option unchanged in the Security Group
  - Click `Add security group rule`. Set Type as `Custom TCP`, Protocol as `TCP`, Port Range as `25565`, Source Type as `Custom`, Source as `0.0.0.0/0`, Description as something memorable like `Minecraft Port`

- Click `Launch Instance` button in bottom right to finish EC2 instance setup

## SSH into EC2 Server
- Wait a few minutes for the EC2 instance to start up, then return to the EC2 main menu (search `EC2` in the upper left search bar)

- Click on `Instances` link in left navbar

- Click on `Instance ID` on your Minecraft Server

- Once you are sure it's running (check `Instance State` status and refresh the page frequently if it hasn't started yet), click the `Connect` button, then `SSH Client`.
  - Read instructions here
  - Double check with instructions, but run `chmod 400 <private SSH key>` if on Unix on your PC. Make sure you are in a directory where you can access the SSH private key. Maybe put that private SSH key in your PATH.
  - Connect to your instance with the public DNS, e.g. `ssh -i "<private key filename>" <public DNS>`, where the values in brackets are stand-in values. Go back to the `Instances` menu for your EC2 instance if you want to double check the public DNS value

- Make sure you can SSh into your EC2 instance before proceeding further.