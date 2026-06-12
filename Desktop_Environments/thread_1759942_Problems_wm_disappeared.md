---
title: "Problems wm disappeared"
date: 2011-05-16
forum: Desktop Environments
---

### Post by cqc on 2011-05-16
when i powered on my pc today i saw that windows manger, cursor and some other things have disappeared. My hard disk has problems with bad sectors, so i guess that could cause it. How can i restore previous state? I have xubuntu 11.04
Thanks in advance

---

### Post by cqc on 2011-05-16
I have soloved it with 
xfwm4 --replace
command[FONT=Verdana]. How can i know what caused this? and how to prevent it?[/FONT]

---

### Post by gsmanners on 2011-05-16
Sounds like you have a hardware problem. I would suggest you start with a disk scan, so:

```
sudo touch /forcefsck
```

Then reboot. That might fix a few things. For more information, check out this page:

[https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)

---

