---
title: "How to install doom 3 with linux binary"
date: 2006-09-21
forum: Gaming &amp; Leisure
---

### Post by WalmartSniperLX on 2006-09-21
Do I have to copy the cds to my hdd or what? how does this work? :confused:

Sorry, real noob here :D

---

### Post by _simon_ on 2006-09-21
Download this: 

[ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1302.x86.run](ftp://ftp.idsoftware.com/idstuff/doom3/linux/doom3-linux-1.3.1302.x86.run)

When finished, open terminal and do

```

sh /path/to/installer/doom3-linux-1.3.1302.x86.run

```

Install to your /home (saves you messing with ownership privledges etc.)

Installation instructions:
--------------------------

The following files need to be copied from the win32 install CDs
to your base/ directory ( md5 sums provided below as reference )
by default, /usr/local/games/doom3/base

71b8d37b2444d3d86a36fd61783844fe  base/pak000.pk4
4bc4f3ba04ec2b4f4837be40e840a3c1  base/pak001.pk4
fa84069e9642ad9aa4b49624150cc345  base/pak002.pk4
f22d8464997924e4913e467e7d62d5fe  base/pak003.pk4
38561a3c73f93f2e6fd31abf1d4e9102  base/pak004.pk4

If you are also installing the Resurrection of Evil Expansion Pack,
you need to copy the following file to your d3xp/ directory
by default, /usr/local/games/doom3/d3xp

a883fef0fd10aadeb73d34c462ff865d  d3xp/pak000.pk4

Localization is not supported on Linux ( only english ), you should not copy over any of the zpak files.

Start the game with the command: doom3
Start the dedicated server with the command: doom3-dedicated

If installed, you can start the Expansion Pack directly from the command line with the command: doom3 +set fs_game d3xp
Or you can select it in the mods menu of the base game.

For troubleshooting and help, see:
[http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/)

---

### Post by WalmartSniperLX on 2006-09-21
Awesome! Thanks :D

---

### Post by WalmartSniperLX on 2006-09-21
ok well I did everything i was supposed to but it seems i cannot launch the doom3 shell script. The command 'doom3' doest not launch the game. Can anyone please help?

---

### Post by tht00 on 2006-09-21
> **WalmartSniperLX said:**
> ok well I did everything i was supposed to but it seems i cannot launch the doom3 shell script. The command 'doom3' doest not launch the game. Can anyone please help?

If you're trying to launch a command in the directory you are in, you need to use this format:
./command

In this case, ./ points to the folder you are in and then looks for the command there.  Otherwise, it will assume /usr/local/bin (and others).  It won't look in your current folder unless you tell it to.

---

### Post by WalmartSniperLX on 2006-09-21
> **tht00 said:**
> If you're trying to launch a command in the directory you are in, you need to use this format:
./command

In this case, ./ points to the folder you are in and then looks for the command there.  Otherwise, it will assume /usr/local/bin (and others).  It won't look in your current folder unless you tell it to.

Ive already done that and it says there is no such folder or file :confused:

---

### Post by Ferrat on 2006-09-21
Just installed doom3 my self (about 30min ago) 

Try do 

comp$ sudo sh ./doom3-linux-1.3.1302.x86.run
(in the folder that you downloaded it to)

---

### Post by Scyattica on 2007-07-29
> **WalmartSniperLX said:**
> ok well I did everything i was supposed to but it seems i cannot launch the doom3 shell script. The command 'doom3' doest not launch the game. Can anyone please help?

Put Doom 3 disc 1 into your drive, navigate to doom3_1/setup/base, and copy the files there to the /base folder of your installed doom 3. 

Do that on all 3 CDs, then afterwards you should be able to play.

---

### Post by dsdexterds on 2007-09-01
Hi guys, I installed Doom 3 everything went ok, but it wont run I get the following error

Fatal X Error:
  Major opcode of failed request: 136
  Minor opcode of failed request: 2
  Serial number of failed request: 64
XF86DGANoDirectVideoMode

(I have an ATI card by the way)

Can anyone help me?

Thanks in advance

---

### Post by DoktorSeven on 2007-09-01
> XF86DGANoDirectVideoMode

Do you have direct rendering enabled?

Type into a terminal window: 
**glxinfo | grep direct**

If you get "direct rendering: no", search for how to enable 3d rendering with an ATI card.

---

### Post by dsdexterds on 2007-09-01
It is not on, I will search, thanks for the help

---

