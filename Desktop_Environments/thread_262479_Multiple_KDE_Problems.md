---
title: "Multiple KDE Problems"
date: 2006-09-21
forum: Desktop Environments
---

### Post by alexsb on 2006-09-21
Hi everyone,

I am having multiple KDE Problems: 

1) KInfoCenter suddenly gives me information on just a view things, such as IEEE 1394 devices, most other pages such as devices, memory, PCI, sound just show the start page.

2) In System Settings the Module Disks & Filesystems does not work - it displays the error message: "The module Disk & Filesystems could not be loaded" "Possible Reasons: 
* An error occured during your last KDE upgrade leaving an orpahted control module. 
* You have old third party libraries lying around"

I am not aware of any of the described issues.

Thanks in advance,

Alex

---

### Post by yurtos on 2007-04-27
im having the same issue with my Disk & Filesystems menu in System Settings. all i did is upgraded from edgy to feisty with adept manager. my error screenshot [URL="http://img368.imageshack.us/img368/5287/snapshot10qx8.png"]here
[/URL]

i have 3 drives in total 1 ide and two sata1 in total. my os is on a stand alone drive and files on other drives. KInfoCenter shows my partitions correctly but when i try to manually mount any of them i get: 

```
yurtos@rs-intel:~$ sudo mount /dev/sdb1 /home/yurtos/Desktop/sdb1
mount: special device /dev/sdb1 does not exist
```

what am i doing wrong?

EDIT: (much later)
very embarrassed for such a silly post. 
note to others, before posting any question, give it a solid good try before you make a fool of yourself.

---

