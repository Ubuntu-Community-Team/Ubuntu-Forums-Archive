---
title: "Advice on updating please"
date: 2011-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Janeleaper on 2011-07-07
We have an Inspiron Mini, which we bought loaded with Ubuntu 8.04.  This is no longer supported, so I'm thinking of upgrading.  But, looking at the Ubuntu site I'm not sure which of the CDs to order. Can someone give me some advice please?

---

### Post by dFlyer on 2011-07-07
> **Janeleaper said:**
> We have an Inspiron Mini, which we bought loaded with Ubuntu 8.04.  This is no longer supported, so I'm thinking of upgrading.  But, looking at the Ubuntu site I'm not sure which of the CDs to order. Can someone give me some advice please?

If you want to stay with an LTS version then download the 10.04 LTS version.

---

### Post by el_koraco on 2011-07-07
If you're ordering a CD because you have limited bandwidth, and want a long support cycle, then order Ubuntu 10.04 Lucid Lynx, because it has the longest support of all the releases at the moment. 

if you have a good internet speed, download 11.04 and see if you like it. If not, try 10.10.

---

### Post by Janeleaper on 2011-07-07
Thanks.  I already have the 10.04 CD, because I installed it on our two desktop PCs.  I hadn't realised it would be OK for the Dell mini.  I thought I needed a special cd for notebooks.

---

### Post by Janeleaper on 2011-07-07
OK, I'm about to make an even bigger fool of myself.  I've just realised I can't install 10.04 from a disc because the Dell mini doesn't have a disc drive.

What do I do?

---

### Post by gbrainin on 2011-07-07
You have several options.  If you don't have a good/fast internet connection, the easiest would probably be to create a bootable USB stick on one of the desktops, then boot and install from that on the mini.

---

### Post by ugm6hr on 2011-07-09
> **Janeleaper said:**
> Thanks.  I already have the 10.04 CD, because I installed it on our two desktop PCs.  I hadn't realised it would be OK for the Dell mini.  I thought I needed a special cd for notebooks.

If you've already installed it on your desktops - you can use usb-creator (which should be in the menu somewhere).
You just need a 1GB USB flash drive (or bigger).

Then you can boot from the USB by pressing Del (I think) when booting the Mini with the USB plugged in.

10.04 works well with the Mini.

---

### Post by Janeleaper on 2011-07-16
Ok.  I actually bought an external CD drive to install 10.04.  

I installed 10.04 on the mini a couple of hours ago, and everything looks fine, except for the wireless internet connection.

The network manager is showing the message "device not ready". Does anyone have any advice about what I should do to get it to find the internet?

---

### Post by mikewhatever on 2011-07-16
Check out System->Administration->Hardware Drivers. It should be able to download and install the driver for you (usually broadcom), make sure you connect a cable, otherwise it won't work.

---

### Post by ugm6hr on 2011-07-17
> **mikewhatever said:**
> Check out System->Administration->Hardware Drivers. It should be able to download and install the driver for you (usually broadcom), make sure you connect a cable, otherwise it won't work.

Correct - but from memory, 10.04 & 10.10 suffered the same problem.
This required a working cable internet connect (as stated) - but needs to be fixed from the Terminal:
[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)
[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by Janeleaper on 2011-07-17
Thank-you both.  The driver is installed, and there don't appear to be any further issues.

---

