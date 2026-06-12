---
title: "session lasts less than 10 seconds - plz help!"
date: 2008-12-21
forum: General Help
---

### Post by akh00 on 2008-12-21
I recently installed Ubuntu 8.04 Hardy Heron in dual boot with XP. It was fine till today morning when I logged off. when I switched on the system again, I got a message which goes something like this:

"Your session lasted less than 10 seconds. If you haven't logged off yourself, then maybe there is an installation problem or you are out of disk space. Try using in in a failsafe login to try to fix the problem"

This is the best of what I could remember. I think there's no installation problem as I've been using Ubuntu for more than 10 days now. I installed some applications for support for displaying Telugu language fonts and also I installed a Telugu GNOME desktop today, so I think I'm out of disk space on Linux.

While installing, I accidentally used 2 drives for the installation. Both had 27Gb before installation and now they both show that their capacity is around 10 gb in windows. I cleared both the drives in windows but that isn't the solution, is it? So how do I solve this problem?

---

### Post by 2hot6ft2 on 2008-12-21
> **akh00 said:**
> I recently installed Ubuntu 8.04 Hardy Heron in dual boot with XP. It was fine till today morning when I logged off. when I switched on the system again, I got a message which goes something like this:

"Your session lasted less than 10 seconds. If you haven't logged off yourself, then maybe there is an installation problem or you are out of disk space. Try using in in a failsafe login to try to fix the problem"

This is the best of what I could remember. I think there's no installation problem as I've been using Ubuntu for more than 10 days now. I installed some applications for support for displaying Telugu language fonts and also I installed a Telugu GNOME desktop today, so I think I'm out of disk space on Linux.

While installing, I accidentally used 2 drives for the installation. Both had 27Gb before installation and now they both show that their capacity is around 10 gb in windows. I cleared both the drives in windows but that isn't the solution, is it? So how do I solve this problem?
So did you try logging in with failsafe mode like it said to?

You could try using the livecd to try and make some room by mounting your install drive and if you have some things cluttering up the desktop like the packages for the fonts and Telugu desktop package either moving them or deleting them.

And what do you mean you cleared the drives in windows?

---

### Post by akh00 on 2008-12-21
I'm a  little confused about what fail-safe mode means. I'm not a very experienced user.

I tried using the live cd but that didn't work. anyway, I haven't installed ANYTHING except those font packages, and now that I think of it, the disk space also might not be problem.

so any other suggestions please?

---

### Post by 2hot6ft2 on 2008-12-21
When you boot up or reboot and you get to the login screen (where you put in your password) you have options one of which is failsafe mode. You simply choose that option and login.

Another option would be to re-install and start over. Other than those I've given already that would be my next choice since no one has jumped it with anything else to try.

---

### Post by akh00 on 2008-12-21
I managed to get in through failsafe mode and then disabled the SCIM which was causing this problem. Here's the error log I get if I try to get in normally:

/etc/gdm/Xsession:Beginning session setup:
setting IM through im-switch for locale=te_IN
start IM through /home/(usrname)/.xinput.d/te_IN linked to/etc/xll/xinit/xinput.dl scim-bridge
Smart Common Input Method 1.4.7

Launching a SCIM daemon with socket frontend...
Loading simple config module...
Creating backend...

**(Seahorse-agent:5466) :CRITICAL **:Couldn't exec/home/(username)/.Xsession:Permisison denied

Can you think of a solution in this case please?thanks a lot

---

### Post by 2hot6ft2 on 2008-12-21
I have no idea, someone else will have to help with that but at least you can login and you seem to have found where the problem is. Good luck.

---

