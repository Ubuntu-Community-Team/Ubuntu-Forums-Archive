---
title: "Gnome Session Restore Forgets Application Parameters"
date: 2009-05-01
forum: Desktop Environments
---

### Post by user2037 on 2009-05-01
The upgrade to 9.04 seems to have enabled session saving and restoring on sign out and sign in. I find it is a nice feature. However, it also forgets the command line parameters used to launch applications. In my case this leads to problems when working with Firefox and custom profiles.

Is there a solution that doesn't include hibernating (instead of sign-out with shutting down) or hacking Gnome?

---

### Post by Protocol84 on 2010-12-13
I am having the same issue but with skype needing arguments for my webcam to work properly. I am looking for the answer and I will let you know if I find anything.

I have found a rather round about way of doing it.

you create a  startup shell script that will shut down the faulty "remembered" app and start the app anew on startup with your desired commands applied, here is my example for skype:

#/bin/bash
killall -9 skype && done
export XLIB_SKIP_ARGB_VISUALS=1 && skype

put it in skype.sh and set it to be run on startup

---

