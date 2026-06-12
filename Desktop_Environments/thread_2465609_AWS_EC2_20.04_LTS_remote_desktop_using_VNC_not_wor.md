---
title: "AWS EC2 20.04 LTS remote desktop using VNC not working entirely - grey screen desktop"
date: 2021-08-06
forum: Desktop Environments
---

### Post by cellrodium on 2021-08-06
Hi,
I just spun up the following AMI in AWS EC2, [ami-019212a8baeffb0fa]("https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Images:imageId=ami-019212a8baeffb0fa")

I followed this [https://ubuntu.com/tutorials/ubuntu-desktop-aws#1-overview](https://ubuntu.com/tutorials/ubuntu-desktop-aws#1-overview), and was able to connect, however, the desktop doesn't look like the Ubuntu desktop.
Its grey with no icons or desktop image.

(See screenshot)

Help is much appreciated.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288936&stc=1[/IMG]

---

### Post by ActionParsnip on 2021-08-06
Try this
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

However, why do you want the full desktop session? What are you doing on the system once you get connected via VNC? I hope you are using an SSH tunnel to secure VNC as the protocol is not encrypted and not secure

Why VNC? Why are you using it?

---

