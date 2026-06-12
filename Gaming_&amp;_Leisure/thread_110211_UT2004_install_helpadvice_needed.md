---
title: "UT2004 install: help/advice needed"
date: 2005-12-30
forum: Gaming &amp; Leisure
---

### Post by jtk on 2005-12-30
I'm trying to install UT2004 on a new 64-bit Breezy Badger install. The install completed, but when I try to run UT, nothing happens (I'm trying to run it by double clicking on ut2004.sh, although I also tried to run the same file through a terminal window with similar results). Now some details on my install:

There was no write access to the default directory, which was usr/local/games or something like that. I couldn't figure out how to login as root, and root is the owner of that directory, so instead I installed it to a new folder in my /home/ directory. Is that OK, or does it need to go in usr/?

There is a dialog box that asks where to put graphical something or other, right after it asks for the install path. What does this dialog refer to? I picked No...

There also appeared to be an error that I could not read behind the install dialog box. Is there an install log somewhere? I'm assuming I'm missing some libraries or something.

Finally, assuming I can get it to run eventually, how would I add it to the Applications drop-down?

Thanks!!

---

### Post by PryGuy on 2005-12-30
There's no need to login as root in Ubuntu, you can do everything that requires the root privilegies typing ```
sudo your_command
```in your terminal window (of course you should type the command or the filename you want instead of "your_command").;) It will ask you for a password, and you'll have to type your user account password, it will work. 

Yet, as far as I know UT2004 doesn't work under the ordinary user account (I wish I knew why?), so you'll have to install it (you know how) and run under the root account using the sudo command!

Good luck!:smile:

---

### Post by siorai on 2005-12-30
I installed it fine into the usr/local/games dir just by using sudo. To run it, I just open a terminal and type in ut2004.

---

### Post by tlc on 2005-12-30
[QUOTE=PryGuy]Yet, as far as I know UT2004 doesn't work under the ordinary user account (I wish I knew why?), so you'll have to install it (you know how) and run under the root account using the sudo command![/QUOTE]

Wrong. I've been playing UT2k4 since it was released as a regular user, never as root. If you can only play as root you've got some permissions messed up somewhere, or your user isn't part of some group it needs to be.

---

### Post by jtk on 2005-12-30
[QUOTE=siorai]I installed it fine into the usr/local/games dir just by using sudo. To run it, I just open a terminal and type in ut2004.[/QUOTE]

I'm not too good with the terminal yet, so I thought that if I did that I would have to use a sudo command every time I wanted to play as well (which I will do if I need to, but I'd prefer not). Did I mention that I'm pretty much a Linux noob? :)

---

### Post by PryGuy on 2005-12-30
[QUOTE=tlc]Wrong. I've been playing UT2k4 since it was released as a regular user, never as root. If you can only play as root you've got some permissions messed up somewhere, or your user isn't part of some group it needs to be.[/QUOTE]Agree!:D Frankly I had no time setting permissions in the UT2004 folder. But anyway, think the best way to see if the game works is to run it under root. And I've read on this forum before that there were problems running UT2004 under the ordinary user account.[QUOTE=jtk]I'm not too good with the terminal yet, so I thought that if I did that I would have to use a sudo command every time I wanted to play as well (which I will do if I need to, but I'd prefer not). Did I mention that I'm pretty much a Linux noob? :)[/QUOTE]As tlc said you'll have to set the right permissions that would allow you to run the game as an ordinary user. But I'd recommend you first run the game as root to make sure it works and then get back here on the forum and tell us about it, and hope we will solve this problem with the permissions.

---

### Post by jtk on 2005-12-30
OK, I'll post back after I get a chance to play with it, probably tonight.

Thanks!

---

### Post by jtk on 2005-12-30
OK, I tried starting ut2004 with sudo... see screenshot for results. Basically, it's not working.

I think I'm gonna uninstall and reinstall using sudo, unless it's apparent to someone else what's wrong...

---

### Post by jtk on 2005-12-30
OK! I tried "sh ut2004" in the directory and got a missing library error. So at least I'm getting somewhere. Kind of a "duh!" moment though...

Edit: Got the missing library installed, and now it works! :) No sudo command needed, either.

---

### Post by PryGuy on 2005-12-31
Please tell me what version of UT2004 do you have? Demo or the full version? I ask you that because I had problems with the demo running it under the regular user account. Guess it was not the latest build of the demo as well, 'cause I took the demo from one of the CDs that come with computer magazines.

If you've just downloaded the linux runtime from the [ut2004.com]("ut2004.com") please tell me the name of the file you've downloaded. The thing that confuses me is that they have the demo version and the one they call "Patch" and I do not want patch I want runtime! I want UT2004 on my Ubuntu too, 'cause demo runs just great! Much faster than the Windows version IMHO.:D

---

### Post by jtk on 2005-12-31
I have the DVD Special Edition version that came with the headphones when UT2k4 first came out... so it's the original version, unpatched. I will patch it eventually, but I'm waiting on a GeForce 6800 from one of my clan buddies, it's not really playable on this MX400 I'm using for now.

---

### Post by siorai on 2005-12-31
I'm using the retail, DVD Editor's Choice Edition with the 3369.2 Megapack. A direct link to the linux version of the Megapack is here: [3369.2 Linux Megapack]("http://treefort.icculus.org/ut2004/ut2004megapack-linux.tar.bz2") The meager instructions for it from [http://www.beyondunreal.com]("http://www.beyondunreal.com") :

"The overworked and underpaid Ryan Gordon has released a UT2004 Mega Pack 3369.2 .bz2 file for our Linux bretheren. Just download and unpack the whole shooting match over your existing UT2004 installation."

---

### Post by Sp@z on 2005-12-31
I have no issues running this game as a regular user. The installer is on disk 1 of the retail CD's not sure where it is on the DVD, I used this link to update the game..........[http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)    ......was much easier than messin with tarballs since I still can't grasp the UNTAR process..............Runs great in Ubuntu, but better in Windoze since I am too scared to update my Nvidia drivers........(broke my xorg last time I did)

---

### Post by PryGuy on 2005-12-31
I'm not kidding if you meant my post of course where I said that the UT2004 runs better (read faster) on my Ubnutu. I have tested it on Intel P4 2GHz Northwood (I know it's old, but anyway) + 512Mb RAM + GeForce 6600 running Windows XP SP2 and on AMD Duron 950 MHz +256Mb RAM + GeForce FX5200 running Ubuntu. I came to conclusion that the last machine was running UT2004 at the same speed (probably faster) and smoother though my Ubuntu box has only 256Mb. It proves that Linux works better with memory.

And, by the way, Happy New Year, friends!!!:D

---

### Post by jtk on 2005-12-31
[QUOTE=siorai]A direct link to the linux version of the Megapack is here: [URL="http://treefort.icculus.org/ut2004/ut2004megapack-linux.tar.bz2"][/QUOTE]

Thanks for that link.

---

### Post by handy on 2006-01-01
Copy the linux install file onto the desktop & run it from there for most reliable intall's apparently.
I got a menu item to call UT2K4 when I installed.
I dual boot with xp pro', & the Ubuntu install is definately not slower than xp.

I play in 1600x1200 res' with everything on to the max. :KS 

I used automatix to install the nVidia drivers, it worked as smooth as...

Cheers,

handy

---

