---
title: "runlevels"
date: 2008-12-25
forum: General Help
---

### Post by thefiestysoldier on 2008-12-25
Can I change my run level i.e (GUI. CLI, single-user) during startup (hotkey??) or do I need to edit a script (I dont want 2 screw my comp)

---

### Post by didac on 2008-12-27
When the GRUB screen appears, press ESC and edit the kernel line for your linux distro. At the end, after splash or whatever, enter your runlevel. The change works only once. It won't screw anything.

Once inside linux you can change your runlevel with 

[CODE] sudo telinit 3 [\CODE]

---

### Post by kevdog on 2008-12-27
The concepts of runlevels -- although valid with others distros and previous versions of ubuntu, is mostly antiquated in todays releases.

---

### Post by lswb on 2008-12-27
ubuntu stopped recognizing runlevels specified on the kernel command line several versions back, except for 'S' or 'single' to start in single-user recovery mode. It is a consequence of migrating to the newer "upstart" system instead of the older svsV "init" startup system. It is fairly easy to add it back to ubuntu by modifying the /etc/event.d/rc-default script. See 

[http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html](http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html)
and
[http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml](http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml)

---

### Post by bodhi.zazen on 2008-12-27
And even when Ubuntu recognized run levels, run level 2-5 are all the same.

To boot to a command line you need to disable GDM (or KDM).

---

