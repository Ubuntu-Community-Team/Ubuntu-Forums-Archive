---
title: "A question"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by catrex on 2008-04-20
I hope i posted well. I`m a new Ubuntu user and i have a problem. All the drivers are working fine  i managed to install my first program(adobe flash) :) except i can`t install my nvidia driver. I went on Google to search for a driver and i followed the instructions three times but i can`t install it. I have an fx5200 nvidia card. If someone knows how can i install it please reply. 

  Thanks in advance and sorry if i posted in the wrong section. ):P

---

### Post by Kevbert on 2008-04-20
You need to activate the restricted drivers manager.  First you need to activate the software source. This can be found under System-Admin-Software Sources Ubuntu Software Tab.  Select Proprietary drivers and Software restricted so both are ticked. Now check under System-Admin-Restricted Drivers are available.  You may need to run Update Manager first.

---

### Post by syczu on 2008-04-20
Did you try to install nvidia driver by system -> administration ->restricted drivers manager?

Or type in terminal :

> sudo apt-get install nvidia-glx

Reboot after install.

---

### Post by catrex on 2008-04-21
Thanks very much, i managed to install the driver and then restart it. But there is a problem again. The machine that is runing ubuntu 7.10 has a 17" Horizon monitor. I think it mas made in China or so..anyway, when i restart the computer it goes to the login screen( i hear that sound) but i don`t see anything. My monitor displays this message"Out of range" and i don`t know what to do. First when i installed ubuntu on my computer, i selected the safe vga mode otherwise it would give me the same message. Maybe a have to buy a new monitor for that machine. :lolflag:

---

