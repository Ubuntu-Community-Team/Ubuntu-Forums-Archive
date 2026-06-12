---
title: "Screen flicker after installing on a Dell Poweredge 1850"
date: 2013-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by astrostar69 on 2013-03-09
Hi Guys,

I have tried installing both Ubuntu 12.04 and CentOS 6.3 (both 64bit) on a PowerEdge 1850 with 16Gb of RAM and both installations went well apart from the fact that every 12 seconds or so the screen flickers (LCD monitor). I have tried various LCD monitors with the same result. I hasten to add that these two distros were separate installations and not installed at the same time !

I have also tried a different 1850 server with the same results.

Initially I though it may have been the screen refresh rate but when I changed it to 75Hz I lost the display alltogether. I'm a newbie when it comes to Linux installations so perhaps I'm missing something obvious. The screen flicker doesn't happen under Windows 7 which I installed to see if the problem remained.
 
Server specs as follows...
 
PE1850
2 x 3.4GHz CPU's
16Gb RAM
2 x 73Gb HDD's
 
Any help greatly appreciated.

Graham

---

### Post by tgalati4 on 2013-03-09
PowerEdge servers normally have Intel graphic chipsets, but they sometimes have ATI or nVidia cards.  What is the output of:

```
lspci | grep VGA
```

Are you plugged into the motherboard VGA port or a PCIe VGA or DVI port?

---

### Post by astrostar69 on 2013-03-10
Hi,

Thanks for the reply - I should have given this info !

It's connected to the motherboard VGA socket. I haven't tried the command above as I'm away from the server at the moment,  but from the spec sheet it says that its an ATI Radeon 7000M. I may try a seperate video card if all else fails and see whether this cures the problem

Graham

---

### Post by astrostar69 on 2013-03-10
Hi,

Running the above command i get the following...

VGA compatible controller: Advanced Micro Devices (AMD) nee ATI RV100 QY (Radeon 7000/VE)

Graham

---

