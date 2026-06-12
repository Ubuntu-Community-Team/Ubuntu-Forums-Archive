---
title: "Inspiron 6400 Wireless problems"
date: 2007-06-25
forum: Dell  Ubuntu Support
---

### Post by TheOriginalH on 2007-06-25
Hey all, having had a hard drive die recently, and absolutely hating the slowness of Vista (which came with new laptop), I decided to give Linux a go again after a 4 year break. Sadly I don't "geek out" as much as I used to, and just wanted a functional OS for web dev and office stuff. Have to say that I am absolutely loving ubuntu - quick, clean and functional - what a breath of fresh air!

Sadly though my wireless card doesn't seem to want to play properly. On first install, it seems Ubuntu was recognising that there was a card, but I couldn't select "wireless networks", thus was unable to actually use it.

I followed instructions here: [http://ubuntuforums.org/showthread.php?t=257684](http://ubuntuforums.org/showthread.php?t=257684) , but all that I seem to have achieved is losing the wireless card completely.

This is the only thing holding me back from completely enjoying the Ubuntu experience - any help would be HUGELY appreciated.

Many thanks,

H

---

### Post by neptho on 2007-06-26
What wireless card do you have?  Not every 6400 is the same; I have the 3945, myself:

```
%lspci | grep -i Wireless
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

It will help to know what card you have.  :)

---

### Post by TheOriginalH on 2007-06-26
I'm not sure how reliable the hardware reporting will be, but according to Device Manager I have a 1390 mini pci card...but that could be as a result of my tinkering nes pas?

---

### Post by TheOriginalH on 2007-06-27
kk - looks like it is indeed the 3945 ABG - any idea how I may go about getting that working?

---

### Post by neptho on 2007-06-28
Thed 3945 should work out of the box.  Enable the restricted modules:

Connect ethernet and setup DHCP (if possible), or use the CD, then run:

```
%sudo apt-get install restricted-modules-generic
%sudo depmod -a
```

When you reboot, the Restricted Modules Manager should notify you they are installed, turn on the checkboxes for the 3945.

If you do, however, have the 1390, try [following the information on the 1390 here](http://pervasivecomputing.net/ubuntu_feisty_7_04_on_dell_inspiron_e1505).

---

