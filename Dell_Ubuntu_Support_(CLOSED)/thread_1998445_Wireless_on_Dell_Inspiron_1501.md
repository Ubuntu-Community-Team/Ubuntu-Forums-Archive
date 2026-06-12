---
title: "Wireless on Dell Inspiron 1501"
date: 2012-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nolanread on 2012-06-06
I just installed Ubuntu 12.04 (64-bit) on my Dell Inspiron 1501.  I can't use the wireless.  From what I have found on the internet I need to install the Windows drivers and then use NDISwrapper.  But I don't know where to find the drivers.  Any help would be greatly appreciated.

---

### Post by Verontier on 2012-06-19
Try putting these lines in the Terminal one at a time:

> sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfreeReboot and it should connect.

---

### Post by nolanread on 2012-11-11
I entered those commands into the terminal, but I got the following error message:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any ideas?

---

### Post by wildmanne39 on 2012-11-15
Hi, that usually means you have software center and the terminal open, if this is not the case reboot the system and that should clear it.
Thanks

---

### Post by f1v3 on 2012-11-17
Previously I am also having same problem then I noticed that there are few functions keys are available in Dell laptops and by pressing them I mistakenly off the wireless connection from hardware.

Check on your laptop, there is key in bottom **Fn** written press that key with key of wireless symbol printed(In mine laptop wireless symbol printed is in F2 key).

One ore thing don't forgot to check the light in laptop of wireless connection.

---

