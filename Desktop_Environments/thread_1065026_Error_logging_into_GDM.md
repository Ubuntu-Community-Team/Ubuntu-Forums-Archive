---
title: "Error logging into GDM"
date: 2009-02-09
forum: Desktop Environments
---

### Post by outerlimit1030 on 2009-02-09
I'm currently using 8.10, and whenever I log in using GNOME, I get an error message stating that I have been logged out in less than 10 seconds.
If I log in using GNOME Failsafe, I have no problems.

I can't figure out what the problem is or how to fix it...
Here is a copy of my .xsession_errors file

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/alternatives/xinput-all_ALL.
/etc/X11/xinit/xinput.d/all_ALL: 1: Syntax error: word unexpected (expecting ")")

---

### Post by outerlimit1030 on 2009-02-09
I think the problem may have came from an fsck.

Yessterday (around the time this problem showed up), while booting it did an fsck (mounted 25 times with no check) and it had some errors.
It booted me into a recovery shell to correct some errors.
There were several problems with various things, so I'm wondering if I answered something incorrectly.
I honestly just answered 'y' to everything because I didn't have time to waste and really needed to get my computer booted so I could get to work.

In my case /etc/alternatives/xinput-all_ALL is an exectuable, which I'm not sure if thats correct.

---

### Post by s.unmesh on 2009-11-03
Yesterday i have installed ubuntu 9.10 on my Acer pc (i was using 9.04) now am not able to login with gnome. But failsafe am able to. Some one please help me

---

