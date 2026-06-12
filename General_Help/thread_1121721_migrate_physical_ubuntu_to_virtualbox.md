---
title: "migrate physical ubuntu to virtualbox"
date: 2009-04-10
forum: General Help
---

### Post by IMELucky on 2009-04-10
I have a physical install of Ubuntu on my MacBook. Does anybody know how to move it into a VirtualBox installation?

Thank you for your help!

—IMELucky

---

### Post by mikewhatever on 2009-04-10
Even if it was possible, it probably wouldn't have worked, simply because vbox virtual hardware is not the same as Macbook's.

---

### Post by Grognot on 2009-04-10
I've got no clue about Macs but as long as the Macbook doesn't use some weird Mac version of Ubuntu I don't see why you couldn't just back up the filesystem say using tar. Create a new virtual machine in Vbox, use a linux recovery disk to partition and format the new machine, then simply untar the backup into the filesystem. After than just use grub to write a new bootloader and you might want to exclude /proc and /sys from the tar.
The macbook and virtualbox machines have different hardware but the relevant modules are loaded during boot up.

---

### Post by mikewhatever on 2009-04-10
I guess it would be an interesting experiment, but think it wouldn't work. Let's say there is an ATI card on the macbook. What's going to happen when you load the say system on vbox? Missing hardware errors? Conflicting modules?

---

### Post by bgerlich on 2009-04-10
Actually it works quite well. If you didn't make any changes to config files everything should reconfigure itself automatically. A helpful tutorial:[http://forums.virtualbox.org/viewtopic.php?t=1966](http://forums.virtualbox.org/viewtopic.php?t=1966)

---

