---
title: "How to share a drive for windows computers"
date: 2009-06-03
forum: General Help
---

### Post by DanHorniblow on 2009-06-03
Hi, I have recently just switched from windows vista to ubuntu and i am a complete beginner to Linux.

Is it possible to share an external USB hard drive on my ubuntu machine and then map it as a network drive on the windows based machines?

---

### Post by blueridgedog on 2009-06-03
Welcome to Ubuntu.  Yes, you can share the files via "samba".  The link here covers the setup pretty well:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

The link my signature also covers the process well.  Give it a try and you can come back here for help if you get stuck.

---

### Post by DanHorniblow on 2009-06-04
Thanks thats helped alot

I was also wondering if it was possible to set my ubuntu machine to backup my home directory to another USB hard disk every day. In windows i would simply write a batch file and add it to the scheduled tasks.

Does Ubuntu make use of batch files?

---

### Post by aparigraha on 2009-06-04
Yes, that is also possible using CRON:

[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

and not the exact thing you are asking for, but this is a great backup thread:
[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by blueridgedog on 2009-06-04
I backup my home directory with rsync:

```
rsync -av /home/ /mnt/Backup/Documents --delete
```

In this case, my USB drive is mounted as /mnt/Backup

You can put the rsync command in cron per the previous post.

---

### Post by blueridgedog on 2009-06-04
Just to add a bit...samba can appear to be a challenging task to setup (and the links and howto's cover many variations that can confuse a new user).  The simple basic part is to install samba, then edit the configuration file and share your USB drive.

You setup shares by editing /etc/samba/smb.conf, which can be done by

```
gksudo gedit /etc/samba/smb.conf
```

All configuration options reside in the smb.conf file.

A simple config out of my smb.conf file looks like this:

[documents]
	comment = Documents
	path = /documents
	guest ok = no
	valid users = myaccount
	browseable = no

This lets me access documents as a "share" off of my system.  Note that you will need to create users on your Ubuntu systme that match the users on the windows system (name and password the same) and you will also need to set the samba password as the links I posted describe.

The important thing is to not get frustrated at the process and realize that going into it there will be a great deal of "getting to know" Ubuntu and samba.  When you tackle it, you can post back to this group and tell where you are stuck and do some searching as well.

---

