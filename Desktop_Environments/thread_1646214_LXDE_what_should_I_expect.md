---
title: "LXDE what should I expect?"
date: 2010-12-15
forum: Desktop Environments
---

### Post by Robbyx on 2010-12-15
I installed the LXDE modules from synaptec. I switched sessions and I login again. Initially the lxde screen appears. It quickly switches to the usual desktop for gnome. Currently System shows information about gnome not lxde.

I can see no difference between LXDE and Gnome and so I suspect the switch has not worked or is the initial flash screen the limit of the changes I can expect? I think I have not properly installed lxde and I would appreciate some help to find out what  I have done wrong.

---

### Post by Kognit on 2010-12-17
Hi

Try this: 
```
sudo apt-get install lxde
```

When the installation is finished, log out and choose lxde session. Log in. This should work.

---

### Post by Robbyx on 2010-12-17
Thank you

---

### Post by spamhog on 2010-12-17
The first "LXDE" screen you see perhaps wasn't LXDE per se but its desktop manager, slim.

If it is there, you should already have installed LXDE.  

At login, try to change the desktop environment to LXDE and see.

I don't recall all the details, but when I installed Lucid + LXDE on a couple of comps 6 months ago, slim caused me some problems, so I switched back to gdm. 

If you too have problems with slim, you may want to go back to gdm.
$ sudo nano /etc/X11/default-display-manager

and change the line to read
/usr/sbin/gdm

I now use gdm, and at login I selected LXDE as default. Works fine!

---

