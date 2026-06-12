---
title: "tftp &quot;Permission denied&quot;"
date: 2009-03-25
forum: General Help
---

### Post by TWarn on 2009-03-25
Hi:

I am using Kubuntu 8.04.  I need to tftp a file from windows (or Linux) to my computer.  I have setup a directory, set the permissions (chmod -R 777 FileName) and set owner (chown -R nobody FileName). I have 2 computers, one works and the other returns "Permission denied"

I followed the instructions I got from teh web and set everything up the same on both computers.

Can anyone help, what do you need to know about my problem.

Thanks In advance
Ted

---

### Post by Copernicus1234 on 2009-03-25
Why are you using tftp and not ftp?

---

### Post by TWarn on 2009-03-25
I don't require any security and I just need to send a specific file to the computer to upgrade the application.  I want to transfer it to the computer and then use VNC to install it.

tftp seemed the simplest approach.

---

### Post by jasballz on 2009-03-25
I'm hosting Buddhabuntu on my vsftpd and have the same problem. if you check out that thread you can see my conf file and netstat output plz help! error 530. login :user1 pword: developers or developer try all caps too, idk

---

### Post by TWarn on 2009-03-25
Hi Guys:

Thanks for your help.  It turned out that the issue was the directory name in the setup file (/etc/xinetd.d/tftp) and the directory where the transfer file was to be stored had a different path.

All is well now.

Ted

---

