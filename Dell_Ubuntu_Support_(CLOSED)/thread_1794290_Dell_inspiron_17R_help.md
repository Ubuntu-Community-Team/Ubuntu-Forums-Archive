---
title: "Dell inspiron 17R help"
date: 2011-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Stevenwhite1017 on 2011-06-30
hI have a dell Inspiron 17R and i just installed ubuntu 10.04 desktop edition on the laptop, I cannot get my wireless internet to work because it needs a driver. I checked the status with the terminal and it said unclaimed which means it cant find it. Ive tried searching and i havent come up with anything so if anyone could help me it would be appreciated.
       If you need any extra info feel free to ask

---

### Post by Carl.Spackler on 2011-07-20
I have a 17R also..

What wireless card is installed in the machine? Broadcom?

If it is, it is very likely that you will have to connect to a wired network connection that has internet service and go to the Hardware Drivers applet and see if it is able to download the driver from the repository.

FWIW, Mine 17R came with an Intel Centrino WiFi Link 1000 adapter. It worked fine OOB, but I needed 5Ghz support so I upgraded to the Intel Centrino WiFi Link 6200 adapter. It is fairly straight forward to do if you are moderately skilled with small parts and a couple of small screwdrivers. I have several Dell machines that had the Broadcom adapters and I always had trouble of some nature fighting back and forth with either the b34 or STM based drivers and VirtualBox and Flash. It was always something. I have had excellent experience with Intel WiFi cards under Ubuntu. YMMV.

Brian

---

