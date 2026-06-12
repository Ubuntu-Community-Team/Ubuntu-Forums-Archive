---
title: "[help] Xorg-air cannot start"
date: 2006-08-25
forum: Desktop Environments
---

### Post by elvislu on 2006-08-25
I have a radeon 7500 mobile card and installed the aiglx according to 
[http://www.ubuntuforums.org/showthread.php?t=145068&highlight=aiglx+7500](http://www.ubuntuforums.org/showthread.php?t=145068&highlight=aiglx+7500)

When I reboot the system, gdm failed to start, showing that the xserver cannot find my device module: ati, kbd, synaptic...

When I used the startx command in the console, it calls xorg and starts without complanation. So why can't my Xorg-air find the device modules while Xorg works fine??? They're using the same configuration file: /etc/X11/xorg.conf.

---

### Post by elvislu on 2006-08-26
I figured it out and found the solution.
I checked the directory /usr/lib/xorg-air/ and compared it with /usr/lib/xorg/. I found that in /usr/lib/xorg-air/ the subdirectories modules/drivers and modules/input are missing.
That's why Xorg-air complains about the missing module.

Solution: link the corresponding modules in xorg to xorg-air
```
$sudo ln -s /usr/lib/xorg/modules/drivers /usr/lib/xorg-air/modules/drivers
$sudo ln -s /usr/lib/xorg/modules/input /usr/lib/xorg-air/modules/input
```

I don't why the directories are missing. Is it a bug?

---

