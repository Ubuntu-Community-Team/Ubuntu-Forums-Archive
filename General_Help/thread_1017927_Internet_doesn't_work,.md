---
title: "Internet doesn't work,"
date: 2008-12-21
forum: General Help
---

### Post by retskrad on 2008-12-21
I juts installed ubuntu with Wubi and logged in. then I realise iternet isnt working. Suddenly it sayd disconected when connecting to internet. Last time I installed wubu internet worked.
When I right click on the internet thing at the right top, it says Auto eth0 or something, I clicked on it and the internet loads again. Thenn again it says disconected. I have tried amny times to restart. Internet works in windows, but not in ubuntu. Whats going on?


PS:I'm using ubuntu 8.10.

---

### Post by retskrad on 2008-12-21
bump

---

### Post by retskrad on 2008-12-21
bump

---

### Post by lovelyvik293 on 2008-12-21
Please tell about your wifi card.

---

### Post by retskrad on 2008-12-21
I dont have any wifi crad, I just got normal internet, a blue box with some cabels conencted to the computer. its 250kb/s highest.

---

### Post by lovelyvik293 on 2008-12-21
ohh!So you are using the static ip address or the assined by the DHCP.

---

### Post by nlz on 2008-12-21
open a terminal, type: ifconfig 
and post the outcome here..

---

### Post by retskrad on 2008-12-21
> **nlz said:**
> open a terminal, type: ifconfig 
and post the outcome here..

How am I supposed tot hat if i dont have internet?

---

### Post by monkeyking on 2008-12-21
also
[PHP]cat /etc/network/interfaces[/PHP]

please elaborate on your network topology

---

### Post by Jammanuser on 2008-12-21
> **retskrad said:**
> How am I supposed tot hat if i dont have internet?

Simple. Open up a Terminal! :) Applications>Accessories>Terminal

Then type "ifconfig" as already mentioned! :lolflag:

Cheers! :popcorn:

-jam man

:guitar:

---

### Post by retskrad on 2008-12-21
Whewn I copy it, then what? How am I suppose to copy it and paste it in windows?

---

### Post by Jammanuser on 2008-12-21
> **retskrad said:**
> Whewn I copy it, then what? How am I suppose to copy it and paste it in windows?

Well...if ur in Windows right now, ur obviously going to have to first reboot into Ubuntu, and open up the terminal in there to run the command! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by monkeyking on 2008-12-21
paste it in a textfile,
pop in a usb key.
pop out the usb key,
pop the usb key in your computer with net,
then post it here.

---

### Post by retskrad on 2008-12-21
admin3@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:6c:cd:5e  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

admin3@ubuntu:~$

---

### Post by monkeyking on 2008-12-22
also post your

/etc/network/interfaces

---

