---
title: "Easy to use backup tool"
date: 2009-04-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sqlyee on 2009-04-16
I am running 8.10 on a Dell Mini 9. Don't feel comfortable without a backup. Is there a tool to do a bootable disk image out there? I'm thinking something like Carbon Copy Cloner on the Mac.

Thanks.

---

### Post by Tobine on 2009-04-16
I'm not familiar with Carbon Copy Cloner but there are a few programs that are supposed to be like Time Machine. Lifehacker did an article on Back In Time recently [lifehacker.com]("http://lifehacker.com/5212899/back-in-time-does-full-linux-backups-in-one-click")

---

### Post by sqlyee on 2009-04-16
Thanks Tobine, I'm off to check it out. I hope it runs under Ubuntu.

---

### Post by anjilslaire on 2009-04-17
Clonezilla

---

### Post by DJonsson2008 on 2009-04-17
I'm using simple backup and restore, its called Sbackup
AKA simple-backup-config. 'sbackup' in synaptic.

Its worked for me on one restoration/new install so far, 
where I've reinstalled Ubuntu from CD, and then restored 
my home directory, on other occassions I've used it to 
restore usr and var as well. Its been a life saver 
many times for restoring home directory when less than
graceful hardware driver installs have required restoration 
of home directory to get my desktop and bookmarks back.

Inside the compressed backup file it makes it creates a text
file called packages, which contains all the packages in
apps installed on your system. When I did the more full
version of the restore using Sbackup on one occassion, I
did not use simple-restore, Instead I used Archive manager
to uncompress and move the directory over using nautilus.

First making sure the new drive was completely updated,
as well as the original drive I proceded to reinstall
all of the packages which was smoother than I thought
it would be.

Manipulating the packages text file I was able to import it
into synaptic and simply update all missing apps. 

I'm still uncertain if it was neccesary to do anything
other than reinstall the home directory. But my instances
of restoring both var and usr seem to have caused no
major problems either. 

The only downside to sbackup that I can see is no progress 
indicator. It is necessary to open top or gnome-system-monitor
to see if the software is running tar and other components,
as well though you can see from your hard disk light if 
the software is active. 

Simple like it says and it works.

---

