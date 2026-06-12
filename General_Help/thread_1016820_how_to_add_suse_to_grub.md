---
title: "how to add suse to grub ?"
date: 2008-12-20
forum: General Help
---

### Post by turna on 2008-12-20
i installed suse, it writes new grub to my hd. but i couldn't boot ubuntu. then i re-install grub with ubuntu. i can boot ubuntu but it doesn't add suse to grub. how to add manually to menu.lst ? suse installed on (hd0,9)

---

### Post by logos34 on 2008-12-20
If suse is on (hd0,9) -- i.e. sda10:

gksudo gedit /boot/grub/menu.lst

add this to bottom:

> title Suse Linux
configfile (hd0,9)/boot/grub/menu.lst

---

### Post by bodhi.zazen on 2008-12-20
See this thread as well :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by turna on 2008-12-21
thanks.

---

