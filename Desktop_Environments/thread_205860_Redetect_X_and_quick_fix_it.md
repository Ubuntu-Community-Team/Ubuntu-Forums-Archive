---
title: "Redetect X and quick fix it ?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by ss0007 on 2006-06-29
Hi, 
recently , i tried to change my video card, and i found that i need to change my xorg conf file to make it work ,so i reverted back. then i installed new kernel , and again my xserver xorg conf file  needs to be reconfigured.

But , with whatever video card tht i have, whn ubuntu is installed for the first time it goes well and works well .

Can i do this same setup whnever i need to reset my xserver modules?
I cant reinstall my ubuntu , ofcourse ,but can i make ubuntu to redetect my video card and write down the new xorg conf file by itself?

i knew abt a sudo dpkg-recofigure xserver... , but i want ubuntu to re detect and configure by iteself , just like the ubuntu installation does .?

thx 4 ur replies in advance,

---

### Post by ss0007 on 2006-06-29
any suggestions ? pls

---

### Post by ss0007 on 2006-06-30
pls any suggestions ? guys ????
(oh ... this is my first thread , whr i saw no reply !!! )

---

### Post by vazzeroni on 2008-01-15
dpkg-reconfigure xserver-xorg or if you're running 7.10, just remove the config file (sudo rm /etc/X11/xorg.conf), though that won't do as well as the first option.
A little late, but in case anybody else finds this

---

