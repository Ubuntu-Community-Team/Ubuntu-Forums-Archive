---
title: "Bios update Dell Inspiron 600m"
date: 2010-01-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Steve.J on 2010-01-28
I am running into a problem updating my Bios. I cant get through all the commands on the dell site except for the actual install. I get an error when I run the command 

update_firmware

Config Error: Plugin "firmware_addon_dell.dellbios" cannot be loaded: No module named firmware_addon_dell.dellbios


Any help would be awesome

---

### Post by jackashe on 2010-02-20
Hey.  the problem is that its using python 2.6 but the modules are in python 2.5.  See this other forum for the answer by ncubede where (s)he symlinks /usr/bin/python to version 2.5.

[http://ubuntuforums.org/showthread.php?t=1386343&page=2](http://ubuntuforums.org/showthread.php?t=1386343&page=2)

---

