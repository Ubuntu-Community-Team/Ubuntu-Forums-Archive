---
title: "GDM won't start on restart / reboot"
date: 2008-11-26
forum: Desktop Environments
---

### Post by Gabe753 on 2008-11-26
I have seen many users raised the issue previously but have not seen a resolution to the following problem: On reboot, the initial UBUNTU screen is displayed, but then a blank screen with only the mouse pointer appear. In only clue I see is in /var/log/auth.log Nov 26 12:48:37 ariel gdm[28293]: 

pam_nologin(gdm:auth): cannot determine username
Nov 26 13:17:01 gdm[28293]: pam_nologin(gdm:auth): cannot determine username
Nov 26 13:43:08 gdm[5848]: pam_nologin(gdm:auth): cannot determine username
Nov 26 13:43:19 gdm[7917]: pam_nologin(gdm:auth): cannot determine username
Nov 26 14:06:05 gdm[7917]: pam_nologin(gdm:auth): cannot determine username

The desktop has two users logged in remotly via ssh. The system is operational via remote access but the console and the GDM enviroment are out. Please help.....

---

### Post by Gabe753 on 2008-11-26
BTW running 8.0.4 desktop

---

### Post by Xiong Chiamiov on 2008-11-27
There is some interesting reading [here]("http://ph.ubuntuforums.com/showthread.php?t=613359&page=4").

---

### Post by mattvenn on 2009-04-01
I had this issue with 8.10.

I installed geda ([http://www.gpleda.org/](http://www.gpleda.org/)) and following reboot gdm hung before I got to see a login window. Don't know if it's causal.

I read more than I wanted to know about gdm, pam, gconf and gnome-keyring-daemon. After spending about 3 hours fruitlessly trying different things and searching the forums and bug reports I just wiped it all and started again.

I've got a backup of /etc now, so I'm hoping (if I get the courage to install geda again) I'll be able to revert to a working system if it goes wrong again. At least we'll know if it's a config change or something more weird.

Apart from this extremely annoying experience 8.10 is by far the best ubuntu I've used. Well done all!

---

### Post by mattvenn on 2009-04-02
same thing just happened again. Though not after install of geda.
I tried reverting to my old /etc which didn't work.

One thing I had learnt from last time was that gdmgreeter fails with a libgailutil.so missing error. After reinstall this library exists, but now my install is smashed again it has gone.

a clue?

---

### Post by mattvenn on 2009-04-02
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/302857](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/302857)

to replace libgail, I booted from the cd, found libgailutil.so and then copied that back to my installed distro. Hey presto it works again (so far so good anyway)

One thing I found while researching was that the new glibc is meant to replace libgail. 

[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/302913](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/302913)

but there is a problem there.

---

