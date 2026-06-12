---
title: "Quake3 in Feisty"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by ricman123 on 2007-05-13
Hey, I'm having trouble getting quake3 to work in Ubuntu. I have the install disc for quake3 and downloaded linuxq3apoint-1.32b-3.x86.run. I then tried pretty much everything i could find online and still can't get it to work. Anyone know what to do? I just installed Ubuntu about 2 days ago, so I'm pretty new to it. What do I have to do?I have the quake 3 install disc and linuxq3apoint-1.32b-3.x86.run.

---

### Post by kefir on 2007-05-13
[http://www.linux-tutorial.info/modules.php?name=Howto&pagename=Game-Server-HOWTO/quake3.html](http://www.linux-tutorial.info/modules.php?name=Howto&pagename=Game-Server-HOWTO/quake3.html)

Basically just run the pointrelease and then copy the *.pk3 files into it's proper place, the guide explains it more.

---

### Post by ricman123 on 2007-05-13
Alright, so I run the installer for that. It says you need root priviliges so I enter my password. 

Then it looks like this:

eric@eric-desktop:~$ $ sh linuxq3apoint-1.32b-3.x86.run
bash: $: command not found
eric@eric-desktop:~$ sh linuxq3apoint-1.32b-3.x86.run
Verifying archive integrity... All good.
Uncompressing Quake III Arena Point Release 1.32b.................................................................................................................................................

so I then go on and try to copy the files from the cd. Then this is what happens:

eric@eric-desktop:~$ cp /mnt/cdrom/Quake3/baseq3/*.pk3 /usr/local/games/quake3/baseq3
cp: cannot stat `/mnt/cdrom/Quake3/baseq3/*.pk3': No such file or directory

What am I doing wrong?

---

### Post by xzero1 on 2007-05-13
Its possible to run quake3 arena and RTCW using wine directly from the windows current install. Simply change to the quake3 folder and run the executable with wine. Its seems these games do not need the registry to run.

---

### Post by B. Gates on 2007-05-13
> **ricman123 said:**
> so I then go on and try to copy the files from the cd. Then this is what happens:

eric@eric-desktop:~$ cp /mnt/cdrom/Quake3/baseq3/*.pk3 /usr/local/games/quake3/baseq3
cp: cannot stat `/mnt/cdrom/Quake3/baseq3/*.pk3': No such file or directory

What am I doing wrong?
What you're doing wrong is that you're following the instructions too literally. In Ubuntu, the CD would have been mounted at /media/cdrom or /media/cdrom0, just run

ls /media

to see what's available. You might have a problem with Q3 though; a common issue is that the game locks up either at the beginning of a round or at the end. If so, run using WINE.

> **xzero1 said:**
> Its possible to run quake3 arena and RTCW using wine directly from the windows current install. Simply change to the quake3 folder and run the executable with wine. Its seems these games do not need the registry to run.
I actually found Q3 to run better in WINE, since I didn't have that damn lockup issue. I know there's a way around with a different build of Q3 or something, but there were do disadvantages using WINE that I could see.

---

### Post by xzero1 on 2007-05-14
> **B. Gates said:**
> 
I actually found Q3 to run better in WINE, since I didn't have that damn lockup issue. I know there's a way around with a different build of Q3 or something, but there were do disadvantages using WINE that I could see.

You misunderstand. I am running Q3 from the native windows install using WINE.

---

