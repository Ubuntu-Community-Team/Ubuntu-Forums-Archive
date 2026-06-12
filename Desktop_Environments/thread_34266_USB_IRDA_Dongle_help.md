---
title: "USB IRDA Dongle help"
date: 2005-05-14
forum: Desktop Environments
---

### Post by vinnie1 on 2005-05-14
Hi

I hope someone out there can help me.  I have a Sigmetal usb - irda dongle which I cant get to work.  I have done lots of Googling and have found out this dongle should be using the module stir4200, when plugged in this module does not automatically load but a few others do.  Even after manually modprobing stir4200 and ircomm, ircomm-tty and then doing irattach irda0 -s dmesg shows no errors and ifconfig -a shows an irda0 as below

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:654 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:1188 (1.1 KiB)  TX bytes:10554 (10.3 KiB)



All i want to do is get my Sony Ericcson K700i and my Sharp Zauras to transfer files and stuff to and from my computer.

Please help someone

 ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by vinnie1 on 2005-05-14
Bump

Am I the only one in the world who cant get this to work ????

Anyone.

---

