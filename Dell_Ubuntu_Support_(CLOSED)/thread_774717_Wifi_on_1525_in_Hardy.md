---
title: "Wifi on 1525 in Hardy"
date: 2008-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CyberCowboy on 2008-04-29
Well after years of trying I've finally talked my father into coming over to Linux, and since he had a Inspiron 1525 (with Vista) I figured it'd be a cake walk since Dell sells this machine with ubuntu (so I thought, didn't notice those were 1525n's)

All went smoothly except the wifi which despite scouring the web I have been unable to find a successful walkthough (including the Dell wiki page)

In case it matters he's running the 64 bit version with an Encrypted LVM.

Does anyone have a reliable walk through for getting the wifi card on the non-ubuntu version of this computer working?  He's visiting through Monday and then going about 4 states away so I need to get this working or he'll go back to Vista more frusterated with linux than he was to begin with :(

---

### Post by adult swim on 2008-04-30
what wifi card do you  have?

---

### Post by CyberCowboy on 2008-04-30
actually I got it squared away last night by following this [http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper) again.  I had missed a few steps before when I did it (Note: don't work on new machines right before bed, you get sloppy)

---

### Post by Jetli2k on 2008-05-01
I have the same problem. My controller is the bcm4310. Tried ndiswrapper, but ndiswrapper only tells me that the driver is installed. It doesn't mention anything about the hardware being present. Also, in the guide it says that I should sudo ndiswrapper -i /tmp/DRIVER/bcmwl5.inf
However, I can't find the bcmwl5.inf. Instead I get the bcmwl6.inf. Don't know if it matters though. What did you do?

---

