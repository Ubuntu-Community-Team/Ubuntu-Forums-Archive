---
title: "Got Ubuntu installed ... but ..."
date: 2009-03-21
forum: General Help
---

### Post by boristhemoggy on 2009-03-21
Well what a piece of cake getting this to dualboot with windows. It installed as smooth as silk on my Dell Inspiron. Can't believe it but chuffed to bits.
There's just a few things I need apart from the obvious: 
A replacement for MSN and AIM which will connect to both of those services. I use them for work.
A CD burner tool
A firewall
A tool like vdownloader for taking files off youtube
A backup program

I'm going to have a look around, but it would be useful if someone has a tried and tested program they could refer me to?

PS Firefox says no programs that contain favourites or bookmarks could be found. How do I import my IE7 favourites?

---

### Post by binbash on 2009-03-21
pidgin
nerolinux, brasero or k3b
iptables or ufw
pytube
Grsync

---

### Post by linuxisevolution on 2009-03-21
pidgin (located in applications >> internet >> pidgin)
k3b (located in add/remove)
Linux has a built in firewall. You can use firestarter to turn it off or manage it at will, which is also located in add/remove.
flash downloader addon for firefox
[backup programs]("http://98.219.177.90/apache2-default/thelinuxhowto/backup.html")

---

### Post by theozzlives on 2009-03-21
> **boristhemoggy said:**
> Well what a piece of cake getting this to dualboot with windows. It installed as smooth as silk on my Dell Inspiron. Can't believe it but chuffed to bits.
There's just a few things I need apart from the obvious: 
A replacement for MSN and AIM which will connect to both of those services. I use them for work.
A CD burner tool
A firewall
A tool like vdownloader for taking files off youtube
A backup program

I'm going to have a look around, but it would be useful if someone has a tried and tested program they could refer me to?

PS Firefox says no programs that contain favourites or bookmarks could be found. How do I import my IE7 favourites?

1. Pidgin, comes with it.
2. Brasaro, comes with it.
3. IPTables, comes with it.
4. **I** Don't use utube.
5. remastersys

---

### Post by linuxisevolution on 2009-03-21
> **theozzlives said:**
> 1. Pidgin, comes with it.
2. Brasaro, comes with it.
3. IPTables, comes with it.
4. Don't use utube.
5. remastersys

Don't ever tell a new user not do something, because they will do it any way:D


How do I know? Personal preference. :)

---

### Post by theozzlives on 2009-03-21
> **linuxisevolution said:**
> Don't ever tell a new user not do something, because they will do it any way:D


How do I know? Personal preference. :)

I was saying I don't use it, duh

---

### Post by linuxisevolution on 2009-03-21
> **theozzlives said:**
> I was saying I don't use it, duh

I'm sorry I can't read minds..

---

### Post by hikaricore on 2009-03-21
I've fixed the post the caused the drama.

Keep it off the help threads, you know better evo.

---

### Post by linuxisevolution on 2009-03-21
> **hikaricore said:**
> I've fixed the post the caused the drama.

Keep it off the help threads, you know better evo.

Drama? I was being sarcastic in a friendly way. :)

---

### Post by Nano_ext3 on 2009-03-21
See my blog of [top 10 linux apps]("http://thelinuxcauldron.wordpress.com/2009/03/20/the-list-ten-apps-that-you-cant-do-without/") ...

Cheers!

_Nano

---

### Post by boristhemoggy on 2009-03-21
I found pidgin and brasero, thanks. Just as well cos there's no Ubuntu package for pidgin that I could find for download,
Pytube download doesn't work, just opens a browser full of gobbledegook and I can't work out what the heck I'm supposed to do with grsync.

No matter I'll spend a few days working out what I can for myself.
Thanks for the suggestions.

---

### Post by boristhemoggy on 2009-03-21
One thing I have noticed...the installer did not make a new partition for Ubuntu. It just sits in a windows folder. It does worrk correctly in dual boot mode, but I thought it had to be on a separate partition.
Hey ho

---

### Post by mb_webguy on 2009-03-22
It sounds like you installed Ubuntu using Wubi, which installs Ubuntu within Windows.  That sort of installation is really more for evaluation purposes.  If you decide you really want a dual-boot installation, you'll need to boot your computer from the [LiveCD]("http://www.ubuntu.com/getubuntu/download").  Here's an [Ubuntu installation guide]("http://wysiwyb.blogspot.com/2008/08/world-without-walls-or-fences-pt3.html") I wrote several months ago that discusses a dual-boot setup.

EDIT:  Because I wrote that guide with newbies in mind, I didn't mention the idea of using a separate partition to share data between Windows and Ubuntu.  If you're thinking about really creating a dual-boot system, this is definitely the way to go.  Windows XP only needs about 15GB for the OS and software, Vista needs about 25GB, and Ubuntu needs about 8GB.  The rest of your drive can be used for a shared data partition, formatted as ext3 (if you're planning to use Ubuntu as your primary OS) or ntfs (if you plan to primarily use Windows).

---

### Post by 3rdalbum on 2009-03-22
You don't need any special utilities for downloading video files from within Flash movies. Just let the video buffer to the very end, minimise your browser (do not close it or move away from the page), go into the /tmp directory and the file will be there ready for you to copy or move it to your home directory.

This works on all Flash video sites.

---

### Post by lisati on 2009-03-22
> **3rdalbum said:**
> You don't need any special utilities for downloading video files from within Flash movies. Just let the video buffer to the very end, minimise your browser (do not close it or move away from the page), go into the /tmp directory and the file will be there ready for you to copy or move it to your home directory.

This works on all Flash video sites.

Thanks for that info. I've been using Ubuntu for some time now and hadn't discovered that one yet.....

---

