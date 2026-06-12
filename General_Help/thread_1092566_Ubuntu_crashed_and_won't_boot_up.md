---
title: "Ubuntu crashed and won't boot up"
date: 2009-03-10
forum: General Help
---

### Post by Cuba71 on 2009-03-10
While reading some email attachments using Evolution, Ubuntu froze and I was forced to power down the system.
Now, it boots up all the way to the login screen and then after a message regarding a configuration problem, it freezes again.
I try to re-start using the recovery tool, and got to the same spot.
Any way to reinstall without loosing all my data?
Any help will be greatly appreciated.

Antonio

---

### Post by kidux on 2009-03-10
> **Cuba71 said:**
> While reading some email attachments using Evolution, Ubuntu froze and I was forced to power down the system.
Now, it boots up all the way to the login screen and then after a message regarding a configuration problem, it freezes again.
I try to re-start using the recovery tool, and got to the same spot.
Any way to reinstall without loosing all my data?
Any help will be greatly appreciated.

Antonio
Try booting in the recovery mode, then use the fsck option in the menu. Let it check everything then reboot. It may fix the problem. I've had to do that numerous times after a hard boot because of the way the journaling file system works.

---

### Post by Weeble818 on 2009-03-10
try hitting alt+f4 to get to terminal, then sudo apt-get remove evolution, since evolution is the only thing i can think would do this, and since my computer did this after tinkering with compiz and all I had to do was remove it. 
or!
when in the terminal thing put
/etc/init.d/gdm stop 
then startx. if that works uninstall evolution, then reinstall when you get it working

not sure if it'll work, I'm still a linux noob.

---

### Post by Cuba71 on 2009-03-10
I've already done the recovery reboot and the fsck with no change.
I also removed evolution, and still noting happens after the reboot, besides de messages.

---

### Post by kidux on 2009-03-10
Keep in mine we're trying options other than re-installing first, so this may seem tedious. 

Boot into a live cd, then use gparted to check the partitions. That may work. If not, I'm out of options from my limited experience.

---

### Post by Weeble818 on 2009-03-10
you may be better off just to salvage files via live cd then re install

---

### Post by Cuba71 on 2009-03-10
I can boot up from a flash drive, but I haven't found the way to access the hard drive.
This is a dual boot Vista/ubuntu.

---

### Post by Cuba71 on 2009-03-11
I didn't solve the problem but I was able to recover the data files I needed and re-install Wubi.

I hope it was an operator's error.

---

### Post by carml on 2009-03-11
A suggestion for the future, if you give some specifications about your system, people can give you usefull suggestions. :)

---

