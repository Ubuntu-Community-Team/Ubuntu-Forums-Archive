---
title: "login screen don't show when boot"
date: 2009-05-05
forum: General Help
---

### Post by needhelp123 on 2009-05-05
Hello,

I am using Ubuntu 9.04.

From the moment I first started to using it, it would boot, load ubuntu, then when the part comes for the login screen to show up...

IT DOES NOT SHOW UP.

instead it's like a black screen, keyboard, mouse, nothing does anything to do it. only thing to do it's restart by pressing the power button. I left it for two hours once in case it's loading, but it's not, just a black screen...

I thought it was a problem X.

I did xfix from recovery mode, that fixed it for ONE reboot, afterwards, same black screen.

I did dpkg-reconfigure -phigh xserver-xorg, that works for TWO reboots, afterwards, same black screen.

I used hwd, that didn't work at all. errors everywhere.

I did Xorg -configure. it didn't work when I did "X -org /root/xorg.conf.new", same black screen. I reboot, it worked. but only for ONE reboot.

I don't know what else to try, anyone have any ideas?

Thank You.

---

### Post by uncre8d1 on 2009-07-29
> **needhelp123 said:**
> Hello,

I am using Ubuntu 9.04.

From the moment I first started to using it, it would boot, load ubuntu, then when the part comes for the login screen to show up...

IT DOES NOT SHOW UP.

instead it's like a black screen, keyboard, mouse, nothing does anything to do it. only thing to do it's restart by pressing the power button. I left it for two hours once in case it's loading, but it's not, just a black screen...

I thought it was a problem X.

I did xfix from recovery mode, that fixed it for ONE reboot, afterwards, same black screen.

I did dpkg-reconfigure -phigh xserver-xorg, that works for TWO reboots, afterwards, same black screen.

I used hwd, that didn't work at all. errors everywhere.

I did Xorg -configure. it didn't work when I did "X -org /root/xorg.conf.new", same black screen. I reboot, it worked. but only for ONE reboot.

I don't know what else to try, anyone have any ideas?

Thank You.
linux noob here.  i'm having the same problem, but can't get it to work even for one reboot.  all i have tried is the xfix (don't know how to do the others).  I've been struggling with this for 2 days & am currently reinstalling.  running a business-custom Compaq (rescued/repaired), unsure of hardware but less than 3 yrs. old.  
  My initial install worked great; problems began after I installed a bunch of (packages?), all games/utilities - i don't think there was anything in there to affect the system.  next reboot gave me this problem. HALP HALP!

P.S. i forgot- using a USB mouse. problem?

---

### Post by PcPro12 on 2009-07-29
I'm having the same problem...I'm completely NEW to ubuntu, I've got the pocket guide for ubuntu and was reading that, learned a few commands here and there...

Anyway, I downloaded ubuntu 9.04 and everything worked fine until I found a TO DO list after you upgrade to ubuntu 9.04...some packages to install and others to upgrade...So I followed it, did the commands and upgraded about 36 packages...nothing new installed...just upgraded...and while upgrading I was browsing the applications menu, and my computer froze...mouse, keyboard, everything...had to restart...now, it won't even get to the boot screen...it loads until the logo comes up, and freezes there...sometimes, gets passed the logo and freezes on the next screen, where it says starting ACPI services...

This is like the 5th time it happens...I've reinstalled it a few times...

And I don't know how to do anything that was said above... I wanted to know how to get the terminal or virtual command terminal open...I know how to when ubuntu is started...but not before it loads...

And I'm also using USB mouse and keyboard...

---

### Post by j.bell730 on 2009-07-29
Might wanna write this down if you don't have a way of accessing this page later.
At the black screen, press ctrl+alt+F2, log in, then run these two commands:
```
sudo apt-get update
sudo apt-get upgrade
```
then, try to get X to start:
```
startx
```
Good luck!

---

### Post by PcPro12 on 2009-07-29
My keyboard and mouse freeze though...but I'll try that...thanks

I don't know if this helps or what it did...but after several times of pressing the reset button...and about 30-60 minutes of the linux hard drive (300gb) being unplugged, ubuntu started up and is now working...Although I ran the above command...

sudo apt-get update

and after running I got this for about 21 different packages...I don't know if this has anything to do with my system not starting up...

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: You may want to run apt-get update to correct these problems
```

---

