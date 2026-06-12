---
title: "Slow Boot time"
date: 2006-01-12
forum: Desktop Environments
---

### Post by fritz_monroe on 2006-01-12
I'm new to Ubuntu, and fairly new to LInux.  I've just gotten Ubuntu installed onto my laptop and it's working pretty well.  I've noticed that Ubuntu is a bit slower to boot to a logon screen than XP and I would like to determine if there's a problem, or if it's just a bit slower.

So, is there a way that I can see a log of what the system is doing at boot?

Thanks
F_M

---

### Post by kaamos on 2006-01-12
When the system is booting, you can press ctrl+alt+F1 to see some info on whats going on.

In general, ubuntu is a bit slower to boot than winxp though. This difference is narrowed by the fact that windows will keep on loading stuff after the boot has reached the desktop, but when ubuntu reaches the desktop everything has loaded.

---

### Post by fritz_monroe on 2006-01-12
I'll give the ctrl-alt-f1 thing a shot.  Thanks.

I also came across dmesg.  I saw that I'm loading Bluetooth drivers.  I don't have any Bluetooth anything.  Do you think it would hurt anything to remove Bluetooth from this laptop?

---

### Post by mark_g on 2006-01-13
Try InitNG. It's a way to speed up the boot process. Worked like a charm for me. 

[http://www.ubuntuforums.org/showthread.php?t=80423&highlight=initNG](http://www.ubuntuforums.org/showthread.php?t=80423&highlight=initNG)

---

