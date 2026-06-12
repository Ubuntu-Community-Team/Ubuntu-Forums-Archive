---
title: "Junk instead of Splash screen"
date: 2007-02-13
forum: Desktop Environments
---

### Post by whayong on 2007-02-13
Hi!  I've been trying to figure out if I'm just going to be "stuck" booting Edgy without a splash screen.  I've re-installed Edgy 2x now mostly because I was trying to workout some wireless issues but I've come past that now.  

So on to the next problem.  Everytime I boot or shutdown I get junk/garbage on the screen.  No splash screen, no readable text.  Just a bunch of white boxes flashing quickly.  The screen size is also significantly smaller at this time (about 1 in border all around).  

Is something screwed up or is my video card just not good enough?  A way to fix it?  This is on a Sony Vaio PCG-SRX77.  It's an onboard Intel chip.  I don't have issues running Edgy (graphics wise), except for this minor detail.

I've tried adding VGA=791 to /boot/grub/menu.lst I believe it was, but when rebooted got an error which asked me to choose between 5 or 6 modes.  They were something like 80x40, 80x60 and so on...... I still bot to the login page and quickly undid the VGA=791 thing.

Please help.  Thanks!

---

### Post by veloce on 2007-02-13
It does sound like a video thing.  With most Intel graphics you need to run 915resolution to get the higher graphics modes.  Do you know what the video card is?

apt-get 915resoultion

Though I can't remember which repository it is in.

Default settings worked for me.  If they don't for you you need to edit the file:

/et/default/915resolution

Instructions are in the file.

---

### Post by whayong on 2007-02-14
from lspci

00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 11)

---

### Post by veloce on 2007-02-14
Re reading your original post, do you get reasonable resolutions once you're into gnome? This would imply that 915resolution is already working.

The next thing to do is to check the horizontal synch and vertical refresh settings in xorg.conf.  Find out what these should be for your monitor and put them in the monitor section.

---

### Post by whayong on 2007-02-14
Yes, everything works fine aside from the spalsh screen which I don't see at all.

> check the horizontal synch and vertical refresh settings in xorg.conf. Find out what these should be for your monitor and put them in the monitor section.

How do I go about doing this?  I'm still learning how to get around and get things done in linux.  

BTW, this is a laptop.

---

### Post by igknighted on 2007-02-14
I don't think this is a bug specific to your intel graphics.  I have an ATI x800 and experience a similar glitch in the splash screens.  Also when I used an NVIDIA FX-5500 the same issue was there.  In fact, the only time I have seen the usplash work is on my friends computer, which ironically uses intel graphics.  I am led to believe that the Ubuntu usplash (and kubuntu and xubuntu) is just still buggy, so perhaps with fiesty it will be upgraded.

---

### Post by whayong on 2007-02-14
> **igknighted said:**
> I don't think this is a bug specific to your intel graphics.  I have an ATI x800 and experience a similar glitch in the splash screens.  Also when I used an NVIDIA FX-5500 the same issue was there.  In fact, the only time I have seen the usplash work is on my friends computer, which ironically uses intel graphics.  I am led to believe that the Ubuntu usplash (and kubuntu and xubuntu) is just still buggy, so perhaps with fiesty it will be upgraded.



LOL!  That's too funny!

---

### Post by veloce on 2007-02-14
> **whayong said:**
> 

How do I go about doing this?  I'm still learning how to get around and get things done in linux.  



First find the manual for your laptop screen. Hopefully in the specs it has the horizontal sync and vertical refresh rates.

Next Alt+F2 to get the run command window.  in this type "gksudo gedit /etc/X11/xorg.conf".  this will open your xorg.conf in the editor (after asking for your password).

**Before you make any changes, save a copy!**

Find the Monitor section and add the lines:

       HorizSync       a-b
       VertRefresh     c-d

where a to d are the numbers you got from your manual.  Save the file and see what happens next time you reboot.

Good luck.

---

### Post by whayong on 2007-02-15
Unfortunately, the manual does say either one.  I can't seem to find anything on it on google as well.

---

### Post by igknighted on 2007-02-15
Are you positive it doesnt say?  Mine is tough to find, but it says:
```
Frequency
FH:30~79KHz
FV:56~75Hz
```
so it might not be exactly like above.  Also try your monitor's manufacturer's page if you can't find it in the manual.

Hmm, for laptops though this might be tough to find... especially on one that old.  I was thinking for an actual monitor manual.  I would guess that SONY *might* have that info, but as the owner of a vaio laptop from that era, don't get your hopes up.

---

### Post by whayong on 2007-02-15
Well, I guess I'm SOL on this one.  Can't seem to find that info, not even on the Sony support website.

---

### Post by veloce on 2007-02-15
In a bizarre turn of events, I find myself in the same situation!  The laptop manual doesn't have this info and I used some from someone elses xorg.conf.  I change from single to dual monitors all the time and somewhere along the way the splash screen has stopped working!

---

### Post by whayong on 2007-02-15
> **veloce said:**
> In a bizarre turn of events, I find myself in the same situation!  The laptop manual doesn't have this info and I used some from someone elses xorg.conf.  I change from single to dual monitors all the time and somewhere along the way the splash screen has stopped working!

Ouch! Hope I didn't jinx it for you.

---

