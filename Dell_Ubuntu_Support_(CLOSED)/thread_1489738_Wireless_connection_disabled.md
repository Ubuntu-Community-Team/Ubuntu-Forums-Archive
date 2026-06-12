---
title: "Wireless connection disabled"
date: 2010-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denverite on 2010-05-21
I installed ubuntu 10.04 on vostro 1500, suddenly my wireless got disabled and I amnt able to figure out how to enable it again. I also have XP on my system on which the wireless works perfect.


Thanks!
Denverite

---

### Post by Anxious Nut on 2010-05-21
Im having the same problem!

Just installed 10.04, used to run linux mint (based on 9.04) which the wireless was working pretty good!

More info:
Not detected in lspci
Said to be disabled in lshw
when preforming a right click on the networking applet, the "Enable wireless" is disabled!

---

### Post by Ivance on 2010-05-22
Same here, after update my wireless card is disabled. Laptop is Dell Inspirion.

iwconfig eth1
--
IEEE 802.11 Access Point: Not-Associated
Link Quality: 5 Signal Level: 0 Noise Level 0


I can't enable wireless from network list.

---

### Post by jarviser on 2010-05-24
> **Ivance said:**
> Same here, after update my wireless card is disabled. Laptop is Dell Inspirion.

iwconfig eth1
--
IEEE 802.11 Access Point: Not-Associated
Link Quality: 5 Signal Level: 0 Noise Level 0


I can't enable wireless from network list.

First, is laptop wireless switch moved to 'on' position? (LHS on Inspiron 1520)

Then if you right-click on network icon in notification area is there an 'enable wireless' checkbox?

Finally, clean install beats upgrade hands-down.

---

### Post by Ivance on 2010-05-24
1. I think that I dont have wireless switch ? Where is it ?

2. When I click on network icon I have enable wireless but it is disabled.

---

### Post by jarviser on 2010-05-24
> **Ivance said:**
> 1. I think that I dont have wireless switch ? Where is it ?


On mine it is a slider on left hand of laptop.  They do vary, sometimes it's a Fn key. If you say which Inspiron it is someone may have one and let you know.  
> **Ivance said:**
> 2. When I click on network icon I have enable wireless but it is disabled.
If the wireless card is not active, either because it's powered off, or if there is no driver for it, yes it will have the Enable Wireless greyed out. Any idea which card is fitted (or take a peek under the cover plate underneath)  Dell online .pdf handbooks are very informative.

---

### Post by Kirkland14 on 2010-05-25
Try hard wiring to you router and go to System>Admin>Hardware Drivers and see if you can get the current driver.  I just put Linux on my 1545 and also did not have wireless connection but it still worked with my win7.  After I got the new drivers it has worked flawlessly. Good Luck

p.s. the wireless switch on mine is F2

---

### Post by Ivance on 2010-05-25
Update fix the thing, F2 too ;) Tnx!

---

### Post by Kirkland14 on 2010-05-25
Great!  I'm glad it worked out for you.  Don't forget to mark this thread as solved.  I've noticed people like when you do this.

---

### Post by rodrigo_acunha on 2010-05-25
i same the same problem but i resolved.

first you need know your drive pci

lspci

if you identify a card

sudo ifconfig wlan0 up

sudo iwlist wlan0 scan

look your connections, but if nothing happend try

etc/NetworkManager/nm-system-settings.conf

edit to:

#[main]
#plugins=ifupdown,keyfile

[ifupdown]
managed=true

worked for me, finally... \\:D/\\:D/

---

