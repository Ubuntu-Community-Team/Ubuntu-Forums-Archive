---
title: "GNOME desktop won't load after normal login - blank brown screen with pointer"
date: 2010-01-22
forum: Desktop Environments
---

### Post by coy.hollingsworth on 2010-01-22
I need a little assistance - for some reason after a reboot am now not able to get my desktop environment (gnome) - does not work in failsafe mode either.

I did some updates to Ubuntu 9.10 and rebooted - i am now in this state.  I have read through some threads without the success of finding my resolution.  The odd thing is that this morning while in my 'solid brown' state the updates window loaded and I was able to see all of today's updates.

I have verified that my xorg.conf file is exactly the same as it was before.  

Any ideas as to the next steps?

---

### Post by erinspice on 2010-01-22
Run ```
sudo dpkg-reconfigure ubuntu-desktop
``` and then log out and back in.

---

### Post by coy.hollingsworth on 2010-01-22
Yeah - i saw that in another post and tried it.  Still no luck.

---

### Post by coy.hollingsworth on 2010-02-02
No luck folks - I performed a complete reinstall and it seems that dual monitors of different sizes is not working well at all with the latest updates.  I have been on Ubuntu exclusively for 2 years now for work and this is a deal breaker.

Windows 7 here we come!  I will try again after the next release in April i guess.

---

