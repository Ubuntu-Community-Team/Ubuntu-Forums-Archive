---
title: "What backup system to use?"
date: 2009-05-24
forum: General Help
---

### Post by rgotten on 2009-05-24
I would like to backup sysncronize my data of a ubuntu server to an linksys NAS storage device...i would like it to do it in incremental way at night. The data should be in the same format as it is on the ubuntu server. At the present moment the ubuntu server data is store as a file server where the windows clients save the data in the ubuntu server...What is recomended? rsync rsnapshop, unison, synkron...
I need the data on the NAS to be readable by the windows clients form the NAS the same way they are form the Ubuntu server?

Thanks

rgotten

---

### Post by khelben1979 on 2009-05-24
Maybe [this document]("http://answers.google.com/answers/threadview/id/715424.html") from Google Answers has anything interesting for you?

It contains several links to different backup solutions. I see the document is from 2006 so I wouldn't be surprised if there is something better out there by this time, but I think it might be useful.

---

### Post by fisheater on 2009-05-24
My gosh, it sounds like you and I are doing the same thing. I have just purchased a d-link DNS-323 for the same sort of set up. I was pleasantly suprized when I found that is runs linux for its OS and has a huge range to 'upgrades'/hacks ([http://wiki.dns323.info/](http://wiki.dns323.info/)). Check you model, may expand its capacity.

As for backup, I have tried two
1.Simple Backup – not bad but a bit strange. Seems to be reliable though. Seems to package the backup into a compressed doc, process runs forever (it seems), and it seems a bit to advanced for my lvl. [http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)

2.Synkron – seems to work like my mind does, just copies the files, then updates the changed files. [http://synkron.sourceforge.net/](http://synkron.sourceforge.net/).

Good luck with it.

FE

---

### Post by leandromartinez98 on 2009-05-24
If you are more or less used to command lines, I recommend rsync. The basic usage is very simple (rsync -av source target), and you will easily be able to build bash scripts containing all backups you want, the way you want, which will be furthermore easily transferable between machines. It can also easily be called from crontab so that automatic backups are made. 

Most important, however, is that using rsync like this will be something that you will be able to do on any linux system you will probably ever use.

---

### Post by colau on 2009-05-24
Thanks all for your tip.

---

### Post by rgotten on 2009-05-25
> **fisheater said:**
> My gosh, it sounds like you and I are doing the same thing. I have just purchased a d-link DNS-323 for the same sort of set up. I was pleasantly suprized when I found that is runs linux for its OS and has a huge range to 'upgrades'/hacks ([http://wiki.dns323.info/](http://wiki.dns323.info/)). Check you model, may expand its capacity.

As for backup, I have tried two
1.Simple Backup – not bad but a bit strange. Seems to be reliable though. Seems to package the backup into a compressed doc, process runs forever (it seems), and it seems a bit to advanced for my lvl. [http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)

2.Synkron – seems to work like my mind does, just copies the files, then updates the changed files. [http://synkron.sourceforge.net/](http://synkron.sourceforge.net/).

Good luck with it.

FE


Which one do you like better..and have you heard about synkron?

---

### Post by kay-man on 2009-05-25
I'm very happy with bacula, in a mixed linux/windows environment. It has saved me on many occasions :)

---

### Post by cmost on 2009-05-25
I like Grsync.  It's in the repositories.  This is a really nice graphical frontend to rsync, a long reliable backup / synchronization tool.  What's great about it is that you can create one or more backup jobs, and then run them via the command line (from a shell script.)  You can schedule your scripts to run via a simple cron job or as a login / logout task.  I highly recommend Grsync for what you're trying to do.

---

### Post by rgotten on 2009-05-25
> **kay-man said:**
> I'm very happy with bacula, in a mixed linux/windows environment. It has saved me on many occasions :)

will this be able to work making copies at nigth from my ubuntu server to my NAS, and is backula doing copies of the files or backup fimes that need to be restore if needed?, also can bacula beuse on a web interface?

rgotten

---

### Post by rgotten on 2009-05-25
> **cmost said:**
> I like Grsync.  It's in the repositories.  This is a really nice graphical frontend to rsync, a long reliable backup / synchronization tool.  What's great about it is that you can create one or more backup jobs, and then run them via the command line (from a shell script.)  You can schedule your scripts to run via a simple cron job or as a login / logout task.  I highly recommend Grsync for what you're trying to do.


Can i do this from my ubuntu server to my NAS..At the present moment my Ubuntu server is a client of the NAS with CIFS....Thanks in advance for your help?

Rgotten

---

### Post by cmost on 2009-05-25
> **rgotten said:**
> Can i do this from my ubuntu server to my NAS..At the present moment my Ubuntu server is a client of the NAS with CIFS....Thanks in advance for your help?

Rgotten

I can't say for certain but I think what you want to do should work well using Grsync.  I've written files from my local Linux partition to my file server which emulates a Windows server via SAMBA.  Since this is a similar scenario to your NAS storage unit I would cautiously answer "yes!"

---

### Post by rgotten on 2009-05-25
> **cmost said:**
> I can't say for certain but I think what you want to do should work well using Grsync.  I've written files from my local Linux partition to my file server which emulates a Windows server via SAMBA.  Since this is a similar scenario to your NAS storage unit I would cautiously answer "yes!"

This migth be a dum question..i like the idea of the gui interface, but can i use it even though i have the ubuntu server..is it possible to open it from a website..??

Thanks

rgotten

---

### Post by cmost on 2009-05-25
Are you talking about accessing the Server from a workstation?  You should be able to remotely log into your Server using a number of tools.  I like to use FreeNX.  Here's a nice tutorial on how to set it up.  Once you've logged into the server, you should be able to run any of its software remotely.

[http://bigbrovar.wordpress.com/2009/05/09/login-graphically-to-your-desktop-from-a-remote-location/](http://bigbrovar.wordpress.com/2009/05/09/login-graphically-to-your-desktop-from-a-remote-location/)

---

### Post by rgotten on 2009-05-25
> **cmost said:**
> Are you talking about accessing the Server from a workstation?  You should be able to remotely log into your Server using a number of tools.  I like to use FreeNX.  Here's a nice tutorial on how to set it up.  Once you've logged into the server, you should be able to run any of its software remotely.

[http://bigbrovar.wordpress.com/2009/05/09/login-graphically-to-your-desktop-from-a-remote-location/](http://bigbrovar.wordpress.com/2009/05/09/login-graphically-to-your-desktop-from-a-remote-location/)


Possible i did not express myself well. Since I have an Ubuntu server, it is run by command line..I use Putty for that. I was saying that i like the idea of a GUI for Grsync...can i run it and see it thru ssh or like webmin that uses a web base interface...in other words...can i see it from a network computer as a GUI

rgotten

---

### Post by fisheater on 2009-05-31
> **cmost said:**
> I like Grsync.  It's in the repositories.  This is a really nice graphical frontend to rsync, a long reliable backup / synchronization tool.  What's great about it is that you can create one or more backup jobs, and then run them via the command line (from a shell script.)  You can schedule your scripts to run via a simple cron job or as a login / logout task.  I highly recommend Grsync for what you're trying to do.

Ok, I have tried Grsync and this is by far the best I have tried to date. I need to read up on how to do incremental backups (pls add a link if you know how to use it!). It is worth a look. And it is nice that it is part of the repositories.

GL~!

Fe

---

### Post by fisheater on 2009-07-22
> **rgotten said:**
> Can i do this from my ubuntu server to my NAS..At the present moment my Ubuntu server is a client of the NAS with CIFS....Thanks in advance for your help?

Rgotten

Ok, need some *basic help here.

I have tried grsync and syncron BUT am unable to see my NAS as an option to save to it. I have my NAS mounted via a shortcut I made in gnome. 

Any suggestions how to make ny NAS visable/accessable to backup?

Pls remember I am very new (read: n00b) to linix.

Thanks

FE

Set up: 9.04 64 bit desktop via lan to ddwrt router to NAS

---

### Post by Cheesemill on 2009-07-22
rsnapshot has always worked great for me :)

---

### Post by e24ohm on 2009-07-29
when is it better to use rsync or mv with a folder mapped to a network location.

currently I run a BASH backup script i created. I already have a remote drive mounted in /mnt, and i use a backup script to tar files, then move the .tar file over into the "/mnt/backup" directory.

---

