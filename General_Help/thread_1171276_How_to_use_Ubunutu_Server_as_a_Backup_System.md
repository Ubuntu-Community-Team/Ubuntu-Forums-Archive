---
title: "How to use Ubunutu Server as a Backup System"
date: 2009-05-27
forum: General Help
---

### Post by scenerio on 2009-05-27
I am looking for a way to run automated backups with my Ubuntu server. I have 3 computers: Ubuntu server, XP desktop and a dual boot XP & Ubuntu Laptop. I would like to use my UB Server to backup my essential files and/or make an image of my other computers harddrive for a quick restore. Also, I would like to backup my own server in case the HDD fails b/c it is 10 years old (I have a 500gig external connected as well). 557812

What program should I use in order to do automatic backups at night of my laptop and desktop? 

Thank you, Any help would be appreciated.

---

### Post by piratebill on 2009-05-27
under linux you could try scp.
I dont remember if scp can do multiple files or not, but a perl script could take care of that issue

under windows this *might* work.  I haven't used windows (other than gaming) in years
[http://www.karenware.com/powertools/ptreplicator.asp](http://www.karenware.com/powertools/ptreplicator.asp)

---

### Post by Girl™ on 2009-05-27
You should read more about *rsync*. I've also heard that [bacula](http://www.bacula.org/en/) is good.

---

### Post by jeromedavies on 2009-05-27
In some ways it depends how complicated you want to get. 

I use Allway Sync on my wifes windows laptop to backup files to an external drive, this could also be used on a network drive.

At work, I use rsync for mirroring files from one server to another, this is an excellent program but can be a little complex to set up.

Or you could look at the cp command (man cp) this has an update option for backing up files. 

Hope some of his helps

---

### Post by jeromedavies on 2009-05-27
Coincidentally, somebody else is asking about rsync here:

[http://ubuntuforums.org/showthread.php?t=1168861](http://ubuntuforums.org/showthread.php?t=1168861)

---

### Post by scenerio on 2009-05-28
Thank you for the help, I am going to look at rsync first. I was also thinking about writing a batch file or something of the sort so that my computer could just FTP any important files to my Ubuntu fileserver. This might help as well.

---

### Post by ghen on 2009-05-28
the files in question to be backed up, will they be in use at the time of backup? like maybe a sql database that runs 24/7 etc.

---

### Post by scenerio on 2009-05-28
I was more thinking of an overnight backup, just to secure my files to another drive in case of failure.

---

