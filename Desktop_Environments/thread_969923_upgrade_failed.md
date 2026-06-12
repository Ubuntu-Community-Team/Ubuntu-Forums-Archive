---
title: "upgrade failed"
date: 2008-11-03
forum: Desktop Environments
---

### Post by teepee on 2008-11-03
i can't seem to get 8.04 to work anymore.  System did an upgrade and it has never been the same.  most recently 242 upgrades were suggested - they took 3 to 4 hours to download and another to install. Install never finished and stopped at 

Setting up gnome-appletes-data (2.22.2-0ubuntu2)

I can't close my "applying changes" screen. I know if I reboot, all hell will break loose.  The last time this happened, I couldn't even reload onto the hard drive.

Can anyone help?

---

### Post by LastChildren on 2008-11-03
Were you trying to update from 8.04 to 8.10?  In my experience, upgrading like that always has issues.  It's usually best to back up your drives and do a fresh install.

---

### Post by teepee on 2008-11-03
system update was prompted -- so i think it was updating my old cd iso version of 8.04 to date.  This happened to me a while ago too

---

### Post by teepee on 2008-11-03
anyone got any ideas???  system is 64b amd with onboard graphics

---

### Post by jobix on 2008-11-04
I had major issues when I upgraded from 6.06 to 8.04 on an AMD64 machine with on-board graphics. I think it was gnome. It failed, I rebooted and lost all the gnome GUI. However, I was still able to use a text-based login. I got some help here on these forums. I started off with: 

sudo apt-get install -f

Then, it would complain about missing dependencies, etc. I would either add or remove stuff as needed, and finally, after a few hours of these iterations, I got it to work.

---

