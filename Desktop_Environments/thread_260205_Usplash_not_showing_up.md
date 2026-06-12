---
title: "Usplash not showing up"
date: 2006-09-18
forum: Desktop Environments
---

### Post by statue on 2006-09-18
Well I finally decided to update the kernal this morning and upon restarting, I noticed I had a black screen with no usplash image/text. Any idea how to get this back?

---

### Post by LotsOfPhil on 2006-09-18
Can you give the output from:

cat /boot/grub/menu.lst

---

### Post by corto72 on 2006-09-18
I have the same problem (See thread [http://ubuntuforums.org/showthread.php?p=1515466#post1515466]("http://ubuntuforums.org/showthread.php?p=1515466#post1515466"))

I can't post the output of "cat /boot/grub/menu.lst" as I can't see anything...](*,) 

Any help welcomed!!!

---

### Post by LotsOfPhil on 2006-09-18
Are you talking about the screen that shows during bootup (before login):
[http://ubuntuforums.org/attachment.php?attachmentid=3197&d=1130424660]("http://ubuntuforums.org/attachment.php?attachmentid=3197&d=1130424660")

Or the one that you type your login info into?
[http://www.pro-linux.de/berichte/jpgs/ubuntu510/loginscreen.png]("http://www.pro-linux.de/berichte/jpgs/ubuntu510/loginscreen.png")

---

### Post by corto72 on 2006-09-18
the second one...

---

### Post by LotsOfPhil on 2006-09-18
Sorry, I don't know what is causing it. Does this link apply to you?

[http://ubuntuforums.org/showthread.php?t=257459]("http://ubuntuforums.org/showthread.php?t=257459")

---

### Post by artinla on 2006-09-18
Could you be more specific as to exactly when the system goes black?  Do you see anything happen at all?  Do you get the GRUB menu?  Does it scroll through the loading of processes/modules/etc?

---

### Post by frankhky on 2006-09-18
I just experienced a similar problem.  Ubuntu just picked up an update.  After rebooting the grub menu came up, then a blank screen with an input out of range message (from lcd monitor).  After a long  wait the login came on.  After logging in I couldn't obtain a wireless connection, so rebooted.  Now it stays on the blank screen (with input out of range message).

---

### Post by corto72 on 2006-09-19
Yes, 

I can see the bios info, the grub menu and it goes through the loding of processes. Just after that, before Gnome starts, I see the cursor in the top lef corner, and that's it... black screen after that. 

I don't believe the thread you mention LotsOfPhil is applicable, as 
 1 - I don't get a blue screen
 2 - I tried login on (without seeing anything) and I heard the welcome sound.
 3 - the screen goes in power saving mode as usual (I have a CRT, so I hear the power beng switched off)
 4 - I did the upgrade on Sunday evening, so it should have been after the fix should was posted. PS: I can't even try to apply the fix, as I can't see a terminal window...

---

### Post by artinla on 2006-09-19
Boot up with your Ubuntu CD

I am assuming that you have an Nvidia card since you mentioned the Sunday update problem.

open a terminal, and type:  

sudo mount /dev/<your linux root partition (example hda1)> /mnt
sudo gedit /mnt/etc/X11/xorg.conf
scroll down to the line that says 'Driver      "nvidia"' 
change it from "nvidia" to "nv"
If you have an ati card, change it to "ati"
save the file and reboot.

you should be able to get a login.  You will then have to reinstall the restricted modules.

---

### Post by corto72 on 2006-09-19
Hi Artinla, 

I finally got it to work, partly thanks to you...

First time I try booting on the CD, I ended up with the same problem. So I rebooted, and downgraded the display resolution (which was before, 640x480, 800x600 and 1024*768) by removing leaving only the 640x480, and that worked...

I then checked as suggested the driver, and it was already set to nv... I decided to leave it as is and only removed the highest resolution in the Screen section. That resolved it

Thanks very much for your help!!!

---

### Post by onewisp on 2006-09-19
Hi,

I am having problem with my ubuntu installation. After the install all screen goes black. The same thing happens when I tried to install ubuntu with the live cd without the safe graphic mode. The thing is, after ubuntu finished installing, I cannot choose safe graphic mode. Help on what to do please! After rebooting(when finishing installation), I only see a blank screen after bios.

---

