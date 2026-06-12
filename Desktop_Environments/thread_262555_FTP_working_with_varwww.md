---
title: "FTP working with /var/www"
date: 2006-09-21
forum: Desktop Environments
---

### Post by dante2010 on 2006-09-21
Hi,

I've just installed Ubuntu server edition so I can have a local LAMP server.  I am trying to get ftp working so I can upload and edit files in the /var/www directory.

I've managed to install vsftpd and I can connect to the IP I've setup for the server from another machine.  

My problem is taht when I login with the user account I created when I installed Ubuntu, it won't let me upload files to anything but the /home/username dir.

How can I set it up so I can upload files to /var/www  ?

---

### Post by dante2010 on 2006-09-21
Anyone able to help me out?

---

### Post by rturner on 2006-09-22
There are a bunch of how-tos here on configuring your ftp server:

[http://ubuntuguide.org/wiki/Dapper#How_to_install_FTP_Server_for_File_Transfer_service](http://ubuntuguide.org/wiki/Dapper#How_to_install_FTP_Server_for_File_Transfer_service)

There are instructions for mapping remote connections to a specific directory.

---

### Post by PriceChild on 2006-09-22
Change the permissions on the upload folder to 777, or make the user/group of the folder the user that your ftp server uses.

---

