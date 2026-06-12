---
title: "Compiz Fusion stopped working"
date: 2009-03-02
forum: Desktop Environments
---

### Post by mmace1 on 2009-03-02
I'm on Ubuntu 8.10.  This is a fresh install (this morning) on my laptop.  Compiz fusion was working very well.  Several times I turned off Compiz Fusion using 'Compiz Switch' : [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)  to troubleshoot Google Earth being unable to start. 

This last time when I tried to turn Compiz back on - it said it was on, but it clearly was still the default window manager.  

Going into System > Preferences > Appearance > Visual Effects and trying to turn on the effects results in the super-helpful error of 'desktop effects could not be enabled'

I've tried going into Synaptic Packager Manager, searching Compiz, and reinstalling everything.  Then, doing the same but with 'complete uninstallaion', then re-installing, same deal.  Also re-installed driver for my video card. 

Trying to run via terminal, and this pops up: 
mark@mark-work:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by pissedoffdude on 2009-03-02
Try resetting compiz's settings:
```
rm -rf ~/.config/compiz
```

Also, post the output of 
```
glxinfo | grep rendering
```

---

### Post by HuaiDan on 2009-03-02
I solved a similar problem awhile back by installing Fusion Icon. Fusion Icon has an option for reloading the window manager. It worked for me.

---

### Post by mmace1 on 2009-03-02
rm -rf ~/.config/compiz

> in terminal, I typed copy/paste that line and it then jumped down the next line - nothing else happened. 

> glxinfo | grep rendering - same, nothing happened. 

I had Fusion Icon installed - it says compiz is already the window manager.  If I ask it to reload the current window manager, I lose everything but my desktop wallpaper & have to pull out the power cord/battery to reboot.

---

### Post by pissedoffdude on 2009-03-02
What kind of graphics card do you have, and how did you install its drivers?

---

### Post by mmace1 on 2009-03-02
[Mobility Radeon X2300], and installed via System > Administration > Hardware Drivers

---

### Post by mmace1 on 2009-03-02
Well whatever it was (that I suspect *I* did) I opted for just a reinstall, it's a good learning experience anyway...

---

