---
title: "screensaver crash"
date: 2005-05-14
forum: Desktop Environments
---

### Post by fsman on 2005-05-14
Each time the screensaver starts it lasts for a few minutes then my machine locks up and I have to do a hardware reset.
I'm running the 2.6.10-5-k7 and tried with -i386 - both have the same problem.
I even did a complete re-install from scratch last night - still getting the lockup.
The only difference I have from a standard install is by following the unoffical starter guide. So I have extra repos (but no backports).
Even selecting a screen saver in preview causes a crash. The AntInspect/spotlight seems to work fine. Biof and busysphere both cause a lockup.

My hardware is Abit KD7A (KT400A); Nvidia 4200.

I would like to submit a bug report, but don't really know what information to supply to help resolve this issue.

Any ideas why this is happening?

---

### Post by edm00se on 2005-09-15
I have the same problem, I have an ATI Radeon 7000 video card. I would also like to know if there's a way of fixing it (go figure).

---

### Post by mortram on 2005-10-25
I've had the same problem.  I have a hunch it's an OpenGL thing and only occurs with certain screensavers.  If you run through the screensaver preview in the preferences, you might find that the screensavers that run the most slowly in the preview will tend to be the ones that take down the system at fullscreen (some SS's will take down my system even in preview).

I pick a low-intensity screensaver and disable the "random" screensaver, choosing "Only One Screensaver".  This has fixed the problem for me in the past.

---

### Post by Samuli on 2005-10-26
I had the exactly same problem on a fresh Hoary install until I installed drivers from ATI's website.

---

### Post by blueturtl on 2005-10-26
Any of you guys happen to install some OpenGL / Mesa or other graphics related packages NOT verified by the Ubuntu team?

That could be an issue.

As for ATI, their drivers suck. If you have an ATI card and are using Linux it's most likely the drivers are the cause. I have Geforce4 Ti4200 and it's absolutely completely 100% stable so I can't think of a reason for it to not work.

edit: Check your BIOS settings to see if there might be problems?
edit2: Is your system overheating by use of these 3D-accelerated screensavers (just to rule out the obvious)?

---

### Post by crossev on 2005-10-26
I am having this problem also.  I tried setting the screensaver to blank and my system locked up while making this selection.  Currently I have disabled the screen saver and their are no more lock ups however this can not be a permanent solution.  Any other suggestions on this problem.  Sadly my graphics card is a Radeon 9200SE


Appreciate any help

Thanks

---

### Post by bonifacio on 2005-10-29
Same problem on a Toshiba M35 with NVIDIA GeForce FX Go5200.  My workaround for now is to use Blank Screen Only mode.  It kinda suck but it was never an issue before when this machine had Hoary.

*The workaround didn't work after all, I step out, return back and my computer is black and froze.  Now I'm frustrated.

---

### Post by tipi on 2005-11-11
Same problem here, after 10 mins of no activity the screen goes black
and only reboot helps,
when i try to turn of the screensaver by system/preferences/screensaver...
the image freezes and ...have to reboot again.
I work on a acer travelmate 2700
with ati igp 9100
did no special installs of drivers and others
system is only up for 2days so everythings pretty default,
I'm an absolute newbie to linux 
help

---

### Post by Nu-Buntu on 2005-11-14
I have a Radeon card...same issue. This needs a fix. It didn't happen in Hoary.

---

### Post by potrick on 2005-11-14
Same problem here, on two different computers. Just this morning I read someone else posting that they switched back to XP over this. Don't want to push too hard, but it seems like a bug that should be looked into. For the record, I'm running a Dell Dimension 2400.

---

### Post by chroniker on 2005-11-25
Same here. If my screensaver starts it locks up, or if I bring up the window to disable/change screensaver my pc locks up.

I'm using an ATI Radeon 9200 on a box that I put together.

---

### Post by YopY on 2005-12-30
Yup, same problem here, locks up whenever selecting a 3D screensaver for longer than a few seconds, then a full lock up. I don't seem to have any trouble with 2D screensavers, it's just the 3D ones that cause me trouble. 

My guess is that it's a driver issue. I've had loads of trouble in the past with re-installing drivers for my Radeon 9200, so I'm not going to try and install new drivers just yet.

I dunno wether the problem appears in 3D games of sorts, since I haven't tried those yet, but I can imagine the same problem happening in there.

---

### Post by Bartender on 2006-01-09
My situation identical to chroniker's - a home-built machine running Radeon 9200SE.  How does one disable screensavers without going to Preferences>Screensavers?
I'm pretty pathetic on the CLI so far.  Took me an hour this morning to figure out that Ubuntu's command for fstab isn't the same as the one in the O'Reilly "Running Linux" book.

---

### Post by Corcorelli on 2006-01-30
I have the same problems. I am running Breezy and have a Radeon 9250 graphics card. The system always locks up when the screensaver is on and my back is turned!

From searching through other threads I've found and tried the following suggestions:
- In BIOS turn of FastWrites for your graphics card
- Uninstall powernowd
- Comment out the VideoRam parameter in xorg.conf

I can't recommend any of these, because they have not worked for me. They have, however, worked for other people.

For the moment I have turned off my screensaver and, so far, no crashes.

---

### Post by Fabiotc on 2007-12-25
In Gutsy, the problem persists...

Radical solution, remove gnome-screensaver and install xcreensaver

---

### Post by vfstaboy on 2007-12-27
Hello,
Has anyone fixed or found more information about this problem? On my install some of the screensavers will crash/reset X and I am back at the login screen.  Others will work but they will be very slow and use a lot of resources.  I'm running Gutsy on a Lenovo T61.

To get back to using "blank screen" I have to run through these steps.

1. aptitude purge gnome-screensaver
2. rm -rf ~/.gconf/apps/gnome-screensaver
3. aptitude install gnome-screensaver

For some reason simply modifying the "%gconf.xml" file in ~/.gconf/apps/gnome-screensaver will not change the setting.

---

### Post by Silent_Thunder on 2008-02-16
If  it helps anyone, this screensaver gave me no problems at all, on a P4 3Ghz, with a Nvidia GF7600GS PCI-E videocard. However (offtopic) does anyone know if it is possible to run this screensaver on a windows OS?

---

