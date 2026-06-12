---
title: "how do I setup ftp access to something besides a home folder"
date: 2009-01-04
forum: General Help
---

### Post by powerplayground on 2009-01-04
How would I setup ftp access to something besides a user account's home folder? I am a noob at vsftpd and I want to share an ntfs drive I have

---

### Post by powerplayground on 2009-01-04
bump, any ideas?

---

### Post by HermanAB on 2009-01-04
The easy/lazy way is to create a new user account and set the home directory of that new user to the directory that you wish to share.  The laborious way is to edit the FTP server configuration file, which could be a pain in the but.  

So, simply install proftpd or vsftpd and don't change its setup - it should work out of the box using my lazy method.

Cheers,

Herman

---

### Post by powerplayground on 2009-01-06
Alright but I can't make a user's home dir somethign that already exists. >.< Do I need to unmount the drive to make it my home dir or can I just edit a text file to change th home dir?

---

### Post by powerplayground on 2009-01-06
Alright I need some help remounting my hard drive. I never deleted the line in my fstab file for the drive, and it still wont mount, what do I have to do in edition to editing my fstab file (btw, this is an ntfs volume.)

---

### Post by powerplayground on 2009-01-06
I got it all working :D

For some odd reason my drives changed their device name when I restarted. And now I realize that if I edit the home dir of a user after i make the account, I can set i to an existing dir :P

---

