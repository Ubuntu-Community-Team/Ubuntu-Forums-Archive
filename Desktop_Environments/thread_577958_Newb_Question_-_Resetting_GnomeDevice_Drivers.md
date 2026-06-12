---
title: "Newb Question - Resetting Gnome/Device Drivers"
date: 2007-10-16
forum: Desktop Environments
---

### Post by jaydeflix on 2007-10-16
Ok.

This is such a newb question, I feel like I should have made sure I was doing things right before doing, instead of now.

So, here's the situation.

Installed Fiesty on a generic Dell.  Started using it, ripping my cds, etc.  Realized I needed more HD space and since it's a slimline case, I needed to move the Ubuntu HD to a different machine which would also fit a 300GB drive.  That's all done, drive boots, gdm won't load, since the video card is now different (now it's a Radeon x1600 AGP card).  

If I boot off the CD, it loads fine, of course.

What is the easiest way to make the HD install re-examine the hardware and reconfig (well, besides simply reinstalling since I'd rather not have to re-rip all the already ripped cds and reinstall whatever software I installed and don't remember)?

I've been doing a bit of searching for an answer, but, I'm coming up either blank or overwhelmed, so, any help is appreciated greatly.

---

### Post by jaydeflix on 2007-10-16
Ok, solved it myself.  I eventually managed to find [https://help.ubuntu.com/community/DebuggingXAutoconfiguration](https://help.ubuntu.com/community/DebuggingXAutoconfiguration) which mentioned the Xorg Autodetection and, after all the miscellaneous commands I've been running, simply renaming the conf file was all I needed to do.  Color me bemused.

---

