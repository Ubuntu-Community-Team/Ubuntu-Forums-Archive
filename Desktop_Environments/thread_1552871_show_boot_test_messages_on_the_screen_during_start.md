---
title: "show boot test messages on the screen during startup"
date: 2010-08-14
forum: Desktop Environments
---

### Post by cccc on 2010-08-14
hi

Howto configure Ubuntu 10.04 to show boot text messages on the screen during startup?

---

### Post by Bucic on 2011-11-16
Bump.

Right now I see only blank screen during startup/shutdown. Startup Manager could configure that but some say it should not be used for newer Ubuntu versions. I removed "quiet splash" from /etc/default/grub.

---

### Post by drs305 on 2011-11-16
Removing 'quiet splash' normally allows the messages to be displayed during boot. Did you run 'update-grub' after you saved the change to /etc/default/grub?

If so, do you happen to have multiple installations? If so, at the Grub menu press 'e' to make sure "quiet splash" isn't still displayed on the 'linux' line.

---

### Post by Bucic on 2011-11-16
* 'update-grub' used
* single install
* "quiet splash" isn't still displayed on the 'linux' line

---

### Post by drs305 on 2011-11-16
Is the setting for 'gfxmode' set to *auto* or something odd?
```
grep "set gfxmode" /boot/grub/grub.cfg
```

You might try setting it to 640x480 just to see if it's a resolution problem. I'd just edit the /boot/grub/grub.cfg file and check the next time you boot. Don't run "update-grub" or you will erase the change.

I'm assuming you are using the 10.04 version of Grub [noparse](1.98)[/noparse], which you can check with "grub-install -v" ).

---

### Post by Bucic on 2011-11-16
> **drs305 said:**
> Is the setting for 'gfxmode' set to *auto* or something odd?
```
grep "set gfxmode" /boot/grub/grub.cfg
```

You might try setting it to 640x480 just to see if it's a resolution problem. I'd just edit the /boot/grub/grub.cfg file and check the next time you boot. Don't run "update-grub" or you will erase the change.

I'm assuming you are using the 10.04 version of Grub [noparse](1.98)[/noparse], which you can check with "grub-install -v" ).
- auto mode
- grub-install (GRUB) 1.99-12ubuntu5

---

### Post by drs305 on 2011-11-16
The 'auto' mode in Grub 1.99 is sometimes a bit problematic. Try changing the value to 640x480 or another supported resolution in grub.cfg.  

If it works, you can make it permanent if desired by uncommenting GRUB_GFXMODE in /etc/default/grub and running 'update-grub'.

---

### Post by Bucic on 2011-11-16
Currently I'm struggling with [LiveCD faster than full install!]("http://ubuntuforums.org/showthread.php?t=1873564") so I'll report back sometime later next week. Thank you for your help!

---

