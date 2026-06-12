---
title: "Set users permissions"
date: 2009-03-06
forum: General Help
---

### Post by jonwcode on 2009-03-06
I need to know how I can set users permissions. To explain I've setup a ubuntu web server. I've got everything but the FTP. So I installed ddclient and got all of that setup and now I went to make a user account for the www folder so that I can login into the FTP and I come to find out that the user that I created don't have permissions to changes or make directorys. So how do I set user permissions? Also I was wondering about how do I delete accounts?


Thanks for the help,

Jon

---

### Post by LegendofTom on 2009-03-06
You can use chmod to change permissions on files and directories.  Also, adduser and deluser are used to add and delete users.

---

### Post by jonwcode on 2009-03-06
So then how would I give and set root powers to a user? Or can there only be one account with root powers?

---

### Post by martrn on 2009-03-06
**What ftp deamon are you running ?**

There is more than one ftp server available in the ubuntu repositories.
vsftpd ftp server see:[ftp-server.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html") is one that ubuntu likes to install if ubuntu installs from the server install.  proftpd see:[proftp server]("http://ubuntuforums.org/showthread.php?t=79588")   is alternative software for people who prefer an FTP server with user access.

Type ```
sudo ps -ef | grep ftp
``` to see what running processes you have with the word 'ftp' in.  The should tell you what ftp server or ftp server deamon you have running on your computer.

PROftpd has its own website with details at :  [http://www.proftpd.org/]("http://www.proftpd.org/")

Vsftpd has its own website with documents and details at : [http://vsftpd.beasts.org/]("http://vsftpd.beasts.org/")
.  Setting up user permission is a matter of editing configuration files or finding a graphical way of doing that.

You could be using any ftp server package, I do not know, and they all have different ways of doing the same thing.

---

### Post by ponyexpress on 2009-03-06
> **jonwcode said:**
> So then how would I give and set root powers to a user? Or can there only be one account with root powers?

System > Administration > Users and Groups
will allow you to modify user privileges ad well as add or remove users.

---

