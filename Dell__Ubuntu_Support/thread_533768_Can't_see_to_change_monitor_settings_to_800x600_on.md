---
title: "Can't see to change monitor settings to 800x600 on inspiron 3800"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by bharris25 on 2007-08-24
I installed Kubuntu on an old inspiron 3800 from live cd.  It took a long time to boot from the live cd and it wouldn't work if I didn't press F4 and change the monitor settings from vga to 800x600x24.  When it would boot the splash screen was off center but when it finally booted up it looked and ran fine, now that it's installed I have no option to change the screen settings before boot and when it boots up I get a light blue screen with nothing on it but I can tell it boots because if I run the pointer all the way to the bottom a line forms on the screen so even though I can't see the arrow I know it's there, please help. I'm new to linux and this is really just a junk laptop that I was experimenting with but it has upgraded ram and actually runs pretty good.

---

### Post by kerry_s on 2007-08-24
500mhz and your running kubuntu, are you insane? on top of that you used the live cd, did that take forever?

anyway's looks like you probably need to install the ati drivers, the screen can do 1024x768x24.

at boot up when you see the screen to pick the kernel press e to edit the boot options, doubt that would help though, it's most likely kubuntu is just still trying to startup and has probably run out of ram.
did you add a swap partion?
how much ram do you have? specs say it can go up to 512mb

i recommend you go xubuntu, use the alternate installer.

[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/xubuntu-7.04-alternate-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/xubuntu-7.04-alternate-i386.iso)

---

### Post by bharris25 on 2007-08-24
I believe it has 383mgb ram, it runs the live cd good it just takes a long time to boot the cd...about 10 minutes yes I did put a 512 swap.  The screen does the same thing if I boot up the live cd without changing the resolution settings by pressing f4.  Oh...it took around 45 min to install, but I think it does boot because it does the same exact thing that the live cd does if I don't change the screen res, and the live cd will boot and then it runs just fine when it boots up, I really just want to see if I can make it work, I like linux and I've been downloading different distros to play with them.

---

### Post by kerry_s on 2007-08-24
well it should work just press "e" at the screen where it has the countdown, move down 1 line press "e" again and add your vga=791(i'm guessing) at the end of the boot line, press enter and "b" to boot it. best of luck to ya. :)

---

### Post by ridgeland on 2007-08-24
Reminds me of learning about xorg.conf.  My second install was for a friend.  I used my monitor for the install then took the PC back and her screen was total yuck.  Also I've swapped monitors on my PC and had very similar issues.
The Ubuntu LiveCD, install CD works well as a second OS to trouble shoot an installed OS.  
Since it seems the liveCD displays OK why not try to copy the settings from it's xorg.conf to the installed xorg.conf  (settings for monitor and display that is)
/etc/X11/xorg.conf

Also I have a 1998 Gateway GP5-200, a 200MHz PC with 192MB or RAM.  It takes 10 minutes to boot but is fine for Firefox, OK for AbiWord.  I use Xubuntu on that one.

---

### Post by kerry_s on 2007-08-25
> **ridgeland said:**
> Reminds me of learning about xorg.conf.  My second install was for a friend.  I used my monitor for the install then took the PC back and her screen was total yuck.  Also I've swapped monitors on my PC and had very similar issues.
The Ubuntu LiveCD, install CD works well as a second OS to trouble shoot an installed OS.  
Since it seems the liveCD displays OK why not try to copy the settings from it's xorg.conf to the installed xorg.conf  (settings for monitor and display that is)
/etc/X11/xorg.conf

Also I have a 1998 Gateway GP5-200, a 200MHz PC with 192MB or RAM.  It takes 10 minutes to boot but is fine for Firefox, OK for AbiWord.  I use Xubuntu on that one.

200mhz 192ram, you should go custom, debian is best on older setups. mines 450mhz 256ram debian base+jwm buildup, mine takes 37secs to boot and i use the basic web stuff.

---

### Post by bharris25 on 2007-08-28
I know for a fact that it boots up now because I can hear the drumbs, I type in the name and password and I hear the music I just can't see anything.  Is there a way to change the monitor settings with a command?  I don't know how to copy over the settings like ridgeland said.

---

### Post by ridgeland on 2007-08-28
Ugh.  I just re-read this thread and saw that you are starting with Kubuntu.  I don't have that installed and don't have a CD for it.  I will download Kubuntu but it will be tomorrow before I am able to have a CD to boot and explain the steps.
I use Ubuntu which is Gnome based not KDE.  Its a different desktop so the steps I would explain for Ubuntu would require more than new bee experience to translate for the KDE desktop.
I'll post back tomorrow.  By the way do you also have a Ubuntu CD to try?

---

### Post by bharris25 on 2007-08-29
I got it to work!!!  I hit e at the countdown and went down 1 line and pressed E to edit, typed vga equals 791...but it didn't work.  and yes I actually used the equals sign but I'm posting this  with my Treo and there isn't an equals sign on my keypad.  Anyway after that I tried my own thing, I entered vga equals 800x600 and it threw up some error messages and then it said it was booting up normally but I thought it was doing the same thing because it dosen't show the Edubuntu loading screen, then the mouse popped up and it had the login screen.  I decided to put Edubuntu on there for the kids, but it's the same as gnome with some different apps and default theme, but I might just put KDE on there for the hell of it now.  Just practicing with that computer so I don't screw up mine.  You should try Linux Mint, I dual booted my main computer with that and Ubuntu.

---

### Post by strabes on 2007-08-29
You'll need to add that vga=791 to the kernel line in your /boot/grub/menu.lst because the options you change while booting in grub are not saved. They are one time only. Just run this:```
sudo kedit /boot/grub/menu.lst
```

---

### Post by bharris25 on 2007-08-29
kinit no resume image doing normal boot
What does that mean because that is what the computer says after I hit ctrl alt F1 after the starting up screen.  It appears that I don't have to edit anything, the computer will boot up if I press ctrl alt F1 after the starting up screen.  It won't boot normal if I just turn it on.  I tried the sudo kedit command and it didn't recognize it.  Any help?

---

### Post by ridgeland on 2007-08-29
What system/desktop are you using?

Kubuntu uses KDE which has kedit, Ubuntu uses Gnome which has gedit  Xubuntu uses XFCE which might use mousepad or something else.  These are simple text editors (kinda like NotePad or WordPad whatever back in MS-land).  If someone tells you to use "vi" run the other way.

/boot/grub/menu.lst
generates the GRUB menu that displays when you boot.  
The first step in editing a system file should always be make a backup.
When you use "e" during the boot you are manually editing a part of menu.lst that is being booted (rather part of a copy, the original is not changed).  To make the edit permanent edit menu.lst.
sudo is required because only root will have read/write for the system file.
Here is part of my menu.lst
```
title Mandriva Linux 2007.1 Spring 7-02-2007 (/dev/sda11)
kernel (hd0,10)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda11  resume=/dev/sda5 splash=silent
initrd (hd0,10)/boot/initrd.img
```
resume points to swap space here.
I haven't noticed Ubuntu putting resume in the kernel line.

The kernel like is where you'll want vga=791

---

### Post by ridgeland on 2007-08-29
I just booted Kubuntu install DVD.
kedit is not there!  It says use "sudo apt-get install kedit"
kate is there for a text editor.
/boot/grub/menu.lst does not exist while running from the install DVD.

---

