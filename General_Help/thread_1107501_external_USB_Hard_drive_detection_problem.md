---
title: "external USB Hard drive detection problem"
date: 2009-03-26
forum: General Help
---

### Post by spandanj on 2009-03-26
System Info: Dell inspiron 6400, ubuntu 8.04

I have an external 320gb [COLOR="DarkRed"]**Simpletech's Signature Mini hard**[/COLOR] drive. Recently (since about 2 weeks ago), I have been encountering several problems with the hard drive. Most of them are with ubuntu alone...

**[SIZE="3"]Problem #1:[/SIZE]** It takes atleast 5 mins or even up 30 mins for Ubuntu to detect that I have attached the hard drive in my USB.

This does not occur in windows xp, vista, or leopard. The hard drive is detected right away every time in these OS's.

**[SIZE="3"]Problem #2[/SIZE]**: WHen I connect to windows xp, although it detects the hard drive without fail, half the time, the prompt shows that the hard drive would be much faster if I use a USB 2.0 port. However, the port is a USB 2.0. And, up until 2 weeks ago, the HD did get detected as a USB 2.0. 

I don't know if this is also the case in Ubuntu WHEN and IF it's detected, since Ubuntu does not show such prompt.


**[SIZE="4"]What I have done to try to solve the problem:[/SIZE]**

1) I did 'chkdsk VOLUME /f' atleast twice in windows xp. Rebooted several times after each time.

2) I did error checking via 'properties' of HD in windows xp. This took much longer. 

3) NOT: I have ***not*** done a defrag since I believe that it would be pointless since Ubuntu doesn't save data on the HD such that it requires Defrag.

[B][COLOR="DarkRed"]
Do you have any suggestions?[/COLOR][/B]

---

### Post by ddrichardson on 2009-03-27
Sounds more like a USB problem than a drive problem. Have you tried it in different ports? Also is you open a terminal and type:```
dmesg
```after pluggin it in you'll get more information.

---

### Post by dcstar on 2009-03-28
> **spandanj said:**
> 
.........
Problem #2: WHen I connect to windows xp, although it detects the hard drive without fail, **half the time, the prompt shows that the hard drive would be much faster if I use a USB 2.0 port. However, the port is a USB 2.0**. And, up until 2 weeks ago, the HD did get detected as a USB 2.0. 
........
Do you have any suggestions?[/COLOR]

If other USB devices work fine then you probably have a faulty drive, or this drive simply draws too much power from your USB port.

---

### Post by spandanj on 2009-03-31
> **dcstar said:**
> If other USB devices work fine then you probably have a faulty drive, or this drive simply draws too much power from your USB port.

yeah,

I called the Simpletech company about the drive and they said that there must be a problem with the chip inside. Unfortunately, they can't replace the drive because I have peeled off the warranty drive off the HD.

so. most likely a problem with the Hard drive inside.

however, I don't understand why it would become hard to detect in ubuntu...

---

