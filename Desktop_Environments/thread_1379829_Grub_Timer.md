---
title: "Grub Timer"
date: 2010-01-13
forum: Desktop Environments
---

### Post by whiskeytango73 on 2010-01-13
Is there a way to make the Grub loader wait indefinitely for an OS choice instead of automatically loading after 10 seconds w/no response on a duel-boot system?

---

### Post by garvinrick4 on 2010-01-13
Instead of 10 in grub config -1

---

### Post by whiskeytango73 on 2010-01-13
How to do that, exactly? New to Linux w/little command line experience.

---

### Post by garvinrick4 on 2010-01-13
Alt/f2  insert "gksudo nautilus" and hit enter. This will get you root in file system.
File system/etc/default/grub   to   GRUB _TIMEOUT=10
Make it -1 and save.

You do seem a little to new to Linux to want to goof around with the file system. Be careful
with what you do or you will be reinstalling a lot. 

Read all the articles you can about GRUB and LIVE CD.

Have a good time with Ubuntu.

---

### Post by whiskeytango73 on 2010-01-13
Yes, I am new, and thank you and everyone else that helps newcomers with your experience and knowledge. I bought a boot-only PC for just this reason. To learn. If I have to re-install a thousand times, it's OK. The duel-boot system is the one I don't want to learn on. Learn on the 32bit FrankenPC, execute well on the 64bit duel-boot. Thanks again.

---

### Post by whiskeytango73 on 2010-01-13
Changed "GRUB_TIMEOUT=10" to "GRUB_TIMEOUT=-1" to no avail. tried to run "update-grub", but displayed that I didn't have the athourity to do that. I'm the only user.

---

### Post by baddog144 on 2010-01-13
Run it as root, with sudo:
```

sudo update-grub

```

---

### Post by whiskeytango73 on 2010-01-13
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="-1"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Ran sudo update-grub successfully, rebooted to see if it worked (three times)-tried "=1" with and w/o quotations... No Beuno.

---

