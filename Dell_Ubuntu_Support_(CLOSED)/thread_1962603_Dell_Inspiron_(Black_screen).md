---
title: "Dell Inspiron (Black screen)"
date: 2012-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RisingMoon on 2012-04-21
I tried to install Ubuntu 11.10 on a 

Dell Inspiron 17R (Q17R)
Processor Core i7-2670M, 2.20 Ghz
Memory 6GB (1333)2s
Screen 17.3 900p WLED HD+
Graphic_Card NVidia GeForce GT 525M, 2GB

... that I bought after seeing that Inspiron 17R is verified by Ubuntu.

After installation I restart the computer and I get to the boot menu and can select Ubuntu. But after that I see a blinking cursor for some seconds and then the screen goes totally black and nothing happens. I can hear the fan running.

I run boot-repair and it didn't solve the problem. It warned thou at the beginning of the process something like ...

"No EFI partition detected. ... Still wana continue.". 

I tried boot-repair 3 times, at the third time the computer dies in the middle of process and now I can't even start the computer. It dies 2 sec after I pushed comp HW start button. Now I need to turn it in for a repair. :(

bootrepair log: 

[http://paste.ubuntu.com/934497/](http://paste.ubuntu.com/934497/)

Then I surfed and found this ...

[I]Some machines (**all Dell laptops**, all new Apple from 2010 on, some Lenovo) 
**have bugs in their UEFI firmware, preventing them from booting (black screen)**. 
Linux Kernel 3.0 (and higher versions) includes patches with workarounds for them.
It is therefore recommended to use a Linux kernel of version 3.0 or higher.
[/I]

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

I tried to install 11.10 that got 3.0 kernel and that didn't work. Maybe 12.04 will work better for a Dell Inspiron 17R and EFI. 

Anyone knows if the Ubuntu-devs is working on making installation of Ubuntu working better for Dell laptops owners or do we have to spend 1+ week trying to get ubuntu work? Will it get better with 12.04? Are they trying to make a solution for EFI?

---

### Post by RisingMoon on 2012-04-22
Okey, I fixed my computer and followed this guide! Very good.

[http://goof848.wordpress.com/2011/12/20/how-to-setup-ubuntu-11-10-on-a-inspiron-17r-n7110/](http://goof848.wordpress.com/2011/12/20/how-to-setup-ubuntu-11-10-on-a-inspiron-17r-n7110/)

The first two steps solved lots for me.

---

