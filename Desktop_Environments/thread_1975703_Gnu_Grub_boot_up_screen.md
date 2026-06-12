---
title: "Gnu Grub boot up screen"
date: 2012-05-07
forum: Desktop Environments
---

### Post by cardiffman28 on 2012-05-07
I dual boot between Vista and 12.04 (Dell Inspiron 6400 for the record).  

On selecting Ubuntu I am always getting a Gnu Grub (v 1.99-21Ubuntu3) screen flash for 10 seconds or so asking me whether I want to launch the generic version, a recovery version, earlier linux versions etc with it defaulting to generic.  

It is all an unhappy reminder of the "improper shut down" screen you get with Windows that invites you to consider recover mode.

How can I stop this Gnu Grub screen please?  I have absolutely no need for it.

Many thanks.

---

### Post by oldfred on 2012-05-07
Is this a wubi install? Where Windows gives you a choice of Windows and Ubuntu and then you get the standard grub menu, even though it is not really used in wubi?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can edit grub and reduce the time from 10 sec, some that have changed to 0 have had issues.

gksudo gedit /etc/default/grub

# change this line:
GRUB_TIMEOUT=10

OR:
I think this works in wubi, but I am not sure.
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

