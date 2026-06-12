---
title: "Where are all the screen savers for KDE4.1???"
date: 2008-11-04
forum: Desktop Environments
---

### Post by at165db on 2008-11-04
I installed Kubuntu 8.10 x86_64 this week, and when I pull up KDE's System Settings menu, click on Desktop and then on Screen Saver I get two choices:
Blank Screen
Random

I did some google-ing and ran:
sudo apt-get install xscreensaver

yet the Screen Saver Settings menu still shows nothing other than Blank Screen.

Has anyone else seen this issue?  Did 8.10 ship with no screen savers and there is some other package I should install?

Thanks!

---

### Post by at165db on 2008-11-05
Anyone else running Kubuntu 8.10 64bit?  Does you KDE have any screen savers?

---

### Post by Wicca on 2008-11-05
I'm running Kubuntu 8.10 32bit and I don't have screensavers either. I think it's a KDE4.1 issue.

---

### Post by Nesnej Trick on 2008-11-05
You need to install the package kscreensaver to get additional screensavers.

Why the screensavers in xscreensavers don't show up as eligible options in the system settings is beyond me.

---

### Post by at165db on 2008-11-05
Thanks, I ended up just installing kscreensaver-xsavers which has xscreensaver-gl and kscreensaver.  I can now see everything in the System Settings menu.

For some reason the GL screen savers performance SUCKS, but I guess that has something to do with TwinView and my 2 monitors.

---

### Post by 6mil928 on 2008-11-09
I too was bummed about the screensavers.  I installed the kscreensaver-xsavers and I still don't see them.  Any ideas?

---

### Post by illunatic on 2010-09-09
Well I found this in one of the install docus. I have no idea how to use it tho because I am a newb.

[FONT=monospace]Where is the X session startup script?
[/FONT]
######################################################################################3
Note: If you do a local installation, you might not see KCometen4 in the Screen Saver Settings module.  In that case, you will need to do one of two things. 

First, you can set the $KDEDIRS environment variable in your X session startup script so it includes your local installation prefix: export KDEDIRS=/usr/local:/usr 

Or second, you can set this for all users by adding your local installation prefix to /etc/kde4rc: [Directories] prefixes=/usr/local  

After that, you may need to manually refresh the system configuration cache by running 'kbuildsycoca4'.  KCometen4 should now appear in Screen Saver Settings.

Edit: Oh... I see this a very old thread. Sorry about the bump!
Still, installed OpenGL screensavers are not showing up in screen saver settings. 
Ideas?

---

