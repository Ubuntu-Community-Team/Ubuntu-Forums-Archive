---
title: "&quot;Create new folder&quot; and &quot;COPY-PASTE&quot; are greyed out, how do i enable it ?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by pranav on 2005-12-14
I have a very basic question....I installed Ubuntu 5.10 on my PC, i can use all the applications but i just** cant make new folders or copy-paste files.** It doesnt happen in the "file-system" partition, nor does it happen in the other hard-disk partions.

Please help!!!

I am absolutely new to Linux, if this question is already answered please direct me to the relevant page. I thank the open-source community for Linux and Ubuntu and the entire cause.

---

### Post by teaker1s on 2005-12-14
sounds like a permission problem 

system-administration-users and groups 
select your user and hit the priviliges tab
check to see everything is ticked

---

### Post by tlc on 2005-12-14
Can you fire up a terminal and create a new folder with:
```
mkdir /home/pravnav/newfolder
```

It sounds like you're trying to make new directories in the root directory. Your regular user only has permissions to make new folders and copy/paste in your home directory. Use 'sudo' for anything else.

---

### Post by pranav on 2005-12-14
Thanks for the prompt reply, i chked the privileges of the user, all are checked now, still no results..

---

### Post by pranav on 2005-12-14
TLC.. the home/pranav folder is the only place where i am able to make new directories.. what about the other partitions of my hard-disk ? please guide me

---

### Post by mcduck on 2005-12-14
Normaly you wouldn't ever need to make folders anywhere else than inside your home directory. That's where you should keep all your personal things. Rest of linux filesystem is reserved for system and installed programs etc. and writing there requires root privileges.

But if you need, you can use 'sudo mkdir <dir name>' to make a directory or 'sudo nautilus' to open file manager window as root.

---

### Post by pranav on 2005-12-14
but i wud need to use the copy-paste at least for the other partions on my hard disk drive, i dont knw how to make it work

---

### Post by teaker1s on 2005-12-14
you need root permission to gain this run in terminal
gksudo nautilus

Sorry my mistake before I didn't realise what you wanted to do I thought it was just a normal folder-the above will work and allow you to also change permissions

---

### Post by teaker1s on 2005-12-14
or create a launcher with command
gksudo nautilus

---

### Post by pranav on 2005-12-14
thanks!

i can create new folders and paste into "home" but i still cant do so in the other partitions of my harddisk, is it possible at all ? pls help

---

### Post by davec99 on 2008-06-21
I realize that this post has been around for a while, but...

I am a pretty experienced Windows user and generally good with hardware as well.  I really like the whole idea and concept of Linux and I have been drawn to Ubuntu's distro because it is realiable, user-friendly, and well-documented.

Why can't I use a partition on my second hard drive without jumping through hoops?  It is mounted and visible in Nautilus, prefaced by gksudo when opening.  This, among a few other things, makes using Linux very frustrating.  I realize there are restrictions that make Ubuntu more stable and secure, but this problem I'm having shouldn't be such a problem.

At the very least, it should be easier to understand why I can't create a directory/folder on the second drive and what to do about it.

I have mounted folders on this drive before, and copied software there, edited fstab to make this mounting happen when booting, etc.  Now, I have gotten rid of all that - I guess /usr on a second drive requires some other tweaking in config files or something.  I'm going to try putting /home there next, and I'm confident I will be able to do this.  Why can't I use the drive now though?  It is visible and mounted, it is formatted in ext3, the swap partition resides happily on that drive in another partition.

It is probably something simple.  Maybe I'm missing some important aspect of Linux and drives and file systems, etc.  But, why isn't the fix for this very obvious?  Linux is not user-friendly for this reason and some related reasons.  I'm just trying to use a hard drive, after all!

---

