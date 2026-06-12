---
title: "Arabic keyboard layout on login screen"
date: 2009-06-12
forum: General Help
---

### Post by saeeddeep on 2009-06-12
A fiend asked me to help !
His keyboard is set to Arabic in Ubuntu login screen, Thus he can NOT write his username and password. I switched to the Recovery Mode, when I started the root shell prompt, I found that the keyboard is not writing in English too. I booted from ubuntu Live CD and I gedit .../etc/default/console-setup and I see:
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""
what else should I do ?

==================

another Q.:
when adding Arabic layout, I see that the default switching option is to press two ALT keys together, but it does not work and it had to be changed to another choice [i.e, Left WIN key for example]. Is there a problem in Ubuntu regarding the Right ALT key, or what ?

---

### Post by saeeddeep on 2009-06-12
anybody there .. I still can NOT login to Ubuntu.
I googled the problem, but still can not solve it?

---

### Post by hansdown on 2009-06-12
Hi saeeddeep.

I have never tried this, but I found a thread that shows this.

it is this thread.



[http://ubuntuforums.org/showthread.php?t=1151141&highlight=keyboard+language](http://ubuntuforums.org/showthread.php?t=1151141&highlight=keyboard+language)

I hope it helps.

---

### Post by saeeddeep on 2009-06-13
Thanks for help.
I want to know:
when booting from Live CD. should I mount my HD [COLOR="Red"]then[/COLOR] run:
$ sudo dpkg-reconfigure xserver-xorg
if so, is it ok to mount my HD where ever I want ( i.e; /mnt/myhd) ?

---

### Post by hansdown on 2009-06-13
Yes, mount it first.

---

