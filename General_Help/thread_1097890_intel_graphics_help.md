---
title: "intel graphics help"
date: 2009-03-16
forum: General Help
---

### Post by mikeonthebeach on 2009-03-16
does any1 know where i can find an intel graphics driver for Ubuntu 8.10, i have a dell laptop (inspiron 640m) to be specific. i am trying to run Super Maryo chronicles which i just successfully installed. i tried playing it and it runs slow as ****

---

### Post by kestrel1 on 2009-03-16
I don't think that a new graphics driver will help.
What amount of Ram do you have & what CPU are you running on.

---

### Post by orlox on 2009-03-16
Actually a driver update would help. Intrepid has serious performance issues with some intel cards:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)

Recently jaunty has shown a very good performance. However, I dont think there's a clean and easy way to install those updated packages in intrepid without an update.

---

### Post by mhgsys on 2009-03-16
I just googled dell inspirion 640  
seems to have 
Processor Intel ® Core™ Duo Processor T2400 (1.83 GHz, 2 MB L2 cache, 667 MHz FSB)

to see which intel graphics card you have try 

```

lspci -v 

```
in a terminal.

and try to find drivers for that.

---

### Post by kestrel1 on 2009-03-16
Not long to wait until Jaunty is out now, just over a month.
Didn't realize about the Intel drivers causing that much problem. Nice link.

---

