---
title: "Ubuntu and FTP?"
date: 2009-05-17
forum: General Help
---

### Post by Willabong on 2009-05-17
I am a total novice with Linux in any form......I wanted to set up a server for my private forum members, and was advised that I should use Ubuntu. So I downloaded the latest version and installed it on my spare computer (works great).
I have worked out that I must install "vsftpd" as a client.
I want to set this computer up as an FTP server.
I would like to make it accessible only to ones who have the URL, and I only want to make one main folder available to them. I don't want them to be able to access anything else on the server.
But I am confused about "Anonymous" and "Local system users".

I also want to allow a Friend to upload to the FTP site.....How do I enable that?
Any step by step advice would be very gratefully received, as I know next to nothing about this subject?:confused:

---

### Post by AnRa on 2009-05-17
[Ubuntu Documentation > Ubuntu 9.04 > Ubuntu Server Guide > File Servers > FTP Server](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)

---

### Post by Willabong on 2009-05-17
Thanks for the link AnRa!  I am still a little confused, for example: How do I allow only one person other than myself, to upload files? Also, is setting it up for local users enough, or can I also make the folder password protected?

---

### Post by Sub101 on 2009-05-17
I would use proftpd as the FTP server and administer it using gprotftpd, setting up users for each member.

---

### Post by Willabong on 2009-05-17
That is going to be very difficult as there are between 600 and a 1000 members of my forum.
All I want to do is set it up so that one of my Moderators and myself can upload files, and everyone else gets a URL via E-Mail to download.
But it needs to be secure!

---

### Post by Sub101 on 2009-05-18
I think it would be very difficult to maintain security without setting up some sort of password.

You could set up a single account and email all the users the username and password?

And another account for the moderators with upload privileges?

---

### Post by jms1989 on 2009-05-18
The users don't need a username and password, just a url fed by apache. A url so they can just click and download, right?

The mods and admins can use a ftp account to upload files. To make a folder password protected, one would need to create a .htaccess and .htpasswd file. I do not know how to create a .htpasswd file but google can help ya.

Just pick a directory on the server and install apache and proftpd and set them up so that they point to that directory. Namely, you can create a user for your mods and point apache to serve that user's home folder so that your users can just have a url to download from. Then you can setup passwrod protection on that same folder with the password file sitting outside the home folder so people can't just read it willy nilly. Once done, just email the username and pass to all your users using a batch mailer.

---

### Post by Sub101 on 2009-05-18
> **jms1989 said:**
> The users don't need a username and password, just a url fed by apache. A url so they can just click and download, right?

The mods and admins can use a ftp account to upload files. To make a folder password protected, one would need to create a .htaccess and .htpasswd file. I do not know how to create a .htpasswd file but google can help ya.

Just pick a directory on the server and install apache and proftpd and set them up so that they point to that directory. Namely, you can create a user for your mods and point apache to serve that user's home folder so that your users can just have a url to download from. Then you can setup passwrod protection on that same folder with the password file sitting outside the home folder so people can't just read it willy nilly. Once done, just email the username and pass to all your users using a batch mailer.

But this will not allow the general security the OP is after, as far as I can tell at least.

---

### Post by Willabong on 2009-05-18
I think I will go with your idea Sub101, it is all I really need!
Is there a command I need to enter to install proftpd and gprotftpd? Are they part of the Ububntu install ?

---

### Post by Sub101 on 2009-05-18
All you need should be:

```
sudo apt-get install gproftpd
```

This should also install proftpd. There are plenty of tutorials on setting up gproftpd but any problems let me know.

---

### Post by Willabong on 2009-05-18
Thanks Sub101. If I have problems (and I probably will), I will get back to you in this thread.
And thanks again to all.

---

