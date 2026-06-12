---
title: "Getting Rid of Windows"
date: 2007-06-28
forum: Dell  Ubuntu Support
---

### Post by clarijan on 2007-06-28
Hi, 

I have a Dell e1705 Notebook and am fed up with Windows XP Media Center Edition. I want to know if it is possible to completely remove windows as my OS and install Ubuntu. I do not want to partition my hard drive; I want windows gone... all of it. I am just worried that in getting rid of windows it will remove the drivers for critical parts of my notebook.

What are people's recomendations for going about this process to remove windows, install ubuntu, and keep my notebook running.

Thanks

---

### Post by Rocket2DMn on 2007-06-28
You can just download the Ubuntu live cd iso, check the md5sum for safety, and burn it to a cd (at a slow speed, also for safety).  Then you can boot from the live cd and reformat your computer with the install - it will setup a small "partition" for swap, but you can use the rest of the drive for ubuntu if you wish.
Drivers are operating system dependent, so you will have to use linux drivers - you can check the compatibility of your separate components online, or even search for problems associated with them on these forums.
Definitely let us know if you have any problems or other questions - the beginners forum may be the best place to get numerous responses.  Welcome to Ubuntu!

---

### Post by Terry of Astoria on 2007-06-28
I say Google whether Ubuntu is well-supported on your laptop. It's likely that it is. I've installed Ubuntu on a few dell laptops now, and no hassles.
I put in "e1705 Ubuntu" and found this:
[http://zapek.com/?p=7]("http://zapek.com/?p=7")

---

### Post by djchandler on 2007-06-28
> **clarijan said:**
> Hi, 

I have a Dell e1705 Notebook and am fed up with Windows XP Media Center Edition. I want to know if it is possible to completely remove windows as my OS and install Ubuntu. I do not want to partition my hard drive; I want windows gone... all of it. I am just worried that in getting rid of windows it will remove the drivers for critical parts of my notebook.

What are people's recomendations for going about this process to remove windows, install ubuntu, and keep my notebook running.

Thanks

clarijan,

Ubuntu may leave your Windows intact when it installs. The Ubuntu Installer will alter the master boot record to a GRUB menu, which will allow a choice of which OS to boot, but only after you've had the pleasure of experiencing Ubuntu with the Trial/Installer CD. I've had problems getting the Installer to overwrite existing partitions. I had to wipe a drive with Dban before the installer would let me use the whole hdd. Somebody more expert than me needs to give you advice; I'm just relating my experience. The other OS was a different Linux distribution, so that may be why the installer acted the way it did, because GRUB was already on the hdd. The great thing about the Trial/Installer CD is it lets you use your computer and run applications before the install process. But don't expect to play mp3 files or any other proprietary media formats that are under strict copyright. Once you have installed Ubuntu, we can help you access and play those files. I use VLC, which also has a Windows version, ([www.videolan.org](www.videolan.org)) as a media player, and it plays everything I've thrown at it, including HDTV digital transport streams recorded by Beyond TV under Windows XP, DivX, wma, wmv, and, of course, mp3. You'll want to check out the MythTV website at [www.mythtv.org](www.mythtv.org) if you have tv recording capabilities to see if MythTV can support your video recording chipset.

Thats all I can help you for now. Good luck, and welcome to the world of Open Source and the Ubuntu Forum. :D

DJ

---

### Post by farueulogy on 2007-06-28
You can, of course, just throw Ubuntu on your whole system by telling it to use the whole disk during the live CD installation.

Not to talk down to you or anyone else - all of your files will be gone if you don't back them up somewhere else. It doesn't ignore document-type files and replace system files. The whole lot will go.

---

### Post by xthund3rh3adx on 2007-06-28
Pop in Ubuntu LiveCD

go to terminal. enter this:

sudo gparted

then totally erase your hard drive, so that it is all "UNALLOCATED SPACE".

Then exit gparted.

Click on install...use whole disk


your all set :)

---

### Post by djchandler on 2007-06-29
> **xthund3rh3adx said:**
> Pop in Ubuntu LiveCD

go to terminal. enter this:

sudo gparted

then totally erase your hard drive, so that it is all "UNALLOCATED SPACE".

Then exit gparted.

Click on install...use whole disk


your all set :)

I knew there must be somebody who knew a better way. Thanks for sharing that. I never thought of using the the partitioning software on the install disk. Duh on me!

Thanks, :D
DJ

---

