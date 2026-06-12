---
title: "K3b in Gnome?!"
date: 2005-12-31
forum: General Help
---

### Post by freddan on 2005-12-31
Would it in some way be possible to use K3b in Gnome? It seems to be quite powerful... Or am I wrong?!

rgds and a Happy New Year.. :p 
/freddan

---

### Post by Norberg on 2005-12-31
Just run sudo apt-get install k3b and it will work with gnome.

---

### Post by DoorGunner on 2005-12-31
The current version may not work. I had errors galore.....go to the site and download from there and find the install instructions.

---

### Post by zoiks on 2005-12-31
I installed it and got it to run without a problem.  It installed ~20 other packages, then required cdrdao additionally, and then asked that I run k3bsetup to get it to run correctly (so that cdrdao could run with root privs).  Then voila.

---

### Post by jdong on 2005-12-31
I used APT to install k3b under GNOME, and it runs great, no extra configuration necessary (except I did a few font tweaks and turned off the KDE Sound System) -- install kcontrol too, so that you can access the KDE control panel under GNOME (ALT+F2, kcontrol)

---

### Post by Horza on 2007-02-03
I installed it with synaptic under dapper lts, without good results.
Installing just k3b left certain things nonfunctional, such as k3setup.

Then I installed all of kde, which which lets k3setup and cd writing work, but not multisession (errors about inability to retrieve session information), or cd erasing (warnings about linux 2.5 or later, and about inability to get exclusive access to /dev/hdd). These two functions also appear to be similarly broken in gnomebaker (erasing broken only when k3b has created the disk in the first place).

It would be quite sad if this mess wasn't cleaned up in time to recruit straying Micro$erfs repelled by the licensing and other annoyances of Vista

---

### Post by Horza on 2007-02-07
It turns out that installing kcontrol is enough to get k3setup and everything else apparently working (for dapper lts), although there still seems to be some screwing around with /etc/fstab to make erasing and multisession work.

---

