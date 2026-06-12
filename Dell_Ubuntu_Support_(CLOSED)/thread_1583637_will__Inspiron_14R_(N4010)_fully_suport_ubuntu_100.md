---
title: "will  Inspiron 14R (N4010) fully suport ubuntu 1004"
date: 2010-09-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rahul_bhise on 2010-09-28
i have decided to by a Dell Inspiron 14R (N4010). i only use ubuntu. and am afraid that if this above laptop do not support ubuntu then i have to use windows (and i don't want to). also the dell people are not selleng this with preloaded ubuntu OS.
the configuration are as follows

T540604IN8-Inspiron(TM) 14R

Inspiron 14R (N4010) Direct Base 
Intel(R) Core(TM) i3-370M (2.4GHz, 4Threads, 3M cache) 
Discount is only valid if the corresponding upgraded item is selected above. 
Limited time promotional offer only. No further discounts apply. 
14.0 Widescreen HD WLED Glossy Display with TrueLife? (1366x768) 
LCD Bezel with 1.3MP Integrated Webcam 
LCD Back Cover - Obsidian Black 
N-Series Label 
Intel® Core? i3 Series Processor Label 
Resource DVD  

Shipping Country (India) 
Integrated 10/100 Ethernet LAN 
7-in-1 Flash Memory Reader: SD, SDHC, MMC, MMC+, xD, MS, MS Pro  
User Manual (English)  
Break the Seal Sticker 
Regulatory Label (India) 
3GB (1 X 1GB + 1 X 2GB) 2 DIMM DDR3 1333Mhz  
For Info only - 1333MHz performance is capped 1066MHz with Pentium, Core i3 and i5 
processors.

320GB 5400RPM Hard Drive 
Optical drive bezel, for DVD+/-RW  
DVD+/-RW Optical Drive 
65W AC Adapter 
Power Cord (India) 
6-cell Lithium Ion Battery 
No Carrying Case 
Shipment Box - Retail  
Intel® HD Graphics (India) 
Integrated Stereo Sound with SRS Premium Sound 
Dell Wireless 1501 802.11b/g/n Half Mini Card  
Dell Wireless 365 Bluetooth Internal (2.1+EDR) Mini-Card 
Dell(TM) Keyboard with Touchpad (English)  
FreeDOS OS with CD kit 
1 Yr Ltd Hardware Warranty, InHome Service after Remote Diagnosis  
# Year 1 Standard POW  
# Yr 1 Ltd Hardware Warranty, InHome Service after Remote Diagnosis  
1 Yr Ltd Hardware Warranty, InHome Service after Remote Diagnosis  
Regional Support Within Asia Pacific Countries For Laptops 
1 Year Technical Phone Support (9am - 5pm Mon-Fri) 
For Info Only: Technical Support 
Technical Support  
For Info Only:Laptop Batteries Carry 1 Year Warranty Only From Invoice Date  
Laptop Batteries Carry 1 Year Warranty Only From Invoice Date  
For Info Only:Dell's Terms and Conditions apply  
Dell's Terms and Conditions apply  
Inspiron-NB Handling & Insurance Charges 
Express Delivery 
Inspiron-NB Handling & Insurance Charges /Express Premium  
Product Handling

---

### Post by mastablasta on 2010-09-28
what kind of card is this: Intel® HD Graphics (India) 
 
Also check if wireless works. the rest should work.
 
here we have 15R (don't have 14R) with very similar specs and it comes Ubuntu preinstalled.

---

### Post by astrobob.tk on 2010-09-28
Hello rahul_bhise,

I own a Dell Inspiron 8600 which has been tested over the past couple of years on Fedora 8 -> 12 & Ubuntu 8.04 -> 10.04 LTS & it has been working great. I recently bought another Dell, a Studio XPS 1640 owned& have Ubuntu 10.04 LTS in dual boot with Win 7, the latter I rarely use. So I assume things should go great with you as well. In any case try checking [Linux on Laptops]("http://www.linux-on-laptops.com/") for more info regarding your laptop. Just select Dell from the menu & check for your laptop if present.

Note: that the name of the laptop might be listed in 2 different forms. For example, when I searched for my studio xps, I tried Studio XPS 16 & Studio XPS 1640. Ctrl+F in firefox will turn on a find bar above the status bar which I think is very helpful to pinpoint stuff.


P.S.: Notice the long list of Inspirons with Dell ;) I think Dell is the best laptop for Linux.

P.S. 2: In case you want to be very cautious, just run a Live disc & try if everything is configured.

Al the best

---

### Post by rahul_bhise on 2010-09-28
i will not be able to check it because first i have to pay then after 10 days it will arrive. they didn't have a piece to showcase in their showroom in our city.

---

### Post by niloferbano on 2010-09-28
I have bought 14r n4010 with same configurations. I have installed ubuntu 10.04. Everything is working fine, but from last two days its not able to connect to wireless network. I may need to re-install ubuntu.

---

### Post by astrobob.tk on 2010-09-28
> i will not be able to check it because first i have to pay then after 10  days it will arrive. they didn't have a piece to showcase in their  showroom in our city.     Its up to you, but I am sure that most Dell's will work just fine if not great. Note that Dell was previously offering many of its laptops, specially the netbooks Ubuntu. Not  sure if they are still doing this. I suggest you contact Dell from their website through the live chat & ask them if the system is compatible with Ubuntu. I think this is the safest way to play it. Anyways keep us updated & good luck :D

P.S.: If things are solved, please state this in a reply & mark the thread as [Solved] under "Thread Tools" for others in a similar situation.

> **niloferbano said:**
> I have bought 14r n4010 with same configurations. I have installed ubuntu 10.04. Everything is working fine, but from last two days its not able to connect to wireless network. I may need to re-install ubuntu.

I believe there's no need to reinstall. Go to System > Administration > Hardware Drivers & check if the drivers are present & activated (green circle on the left of the driver name). If you installed from a disc, just insert the disc & load the Hardware Drivers. It should appear. I assume you didn't activate the drivers yet. In my case of my new Studio XPS 1640, I couldn't get the wireless adapter configured until I installed the drivers.

---

### Post by niloferbano on 2010-09-28
In system->Administrator->Hardware Driver, its showing "Driver is activated but not in use".
I have also tried re-installing the driver, but still have the same problem.

---

### Post by astrobob.tk on 2010-09-28
> **niloferbano said:**
> In system->Administrator->Hardware Driver, its showing "Driver is activated but not in use".
I have also tried re-installing the driver, but still have the same problem.

take note of the name of this driver & the description (for future reference). select it & click remove then close the hardware drivers. Open Synaptic Package Manager & enter "Broadcom STA wireless driver" under Quick Search & select the following packages for installations:
bcmwl-kernel-source
bcmwl-modaliases

Note that both have a ubuntu logo on the right, that is they are Ubuntu supported. Select them & apply for installation & check if things are solved or not.

In the case if they are not, please direct to [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=1569966").
I hope what I suggested solves your problem & that you dont need to refer to the other thread.

---

### Post by xircon on 2010-09-28
If your wireless was working but now isn't try this:

[http://ubuntuforums.org/showthread.php?t=1584063](http://ubuntuforums.org/showthread.php?t=1584063)

look for my post.

---

### Post by niloferbano on 2010-09-29
> **astrobob.tk said:**
> take note of the name of this driver & the description (for future reference). select it & click remove then close the hardware drivers. Open Synaptic Package Manager & enter "Broadcom STA wireless driver" under Quick Search & select the following packages for installations:
bcmwl-kernel-source
bcmwl-modaliases

Note that both have a ubuntu logo on the right, that is they are Ubuntu supported. Select them & apply for installation & check if things are solved or not.

In the case if they are not, please direct to [this thread]("http://www.uluga.ubuntuforums.org/showthread.php?t=1569966").
I hope what I suggested solves your problem & that you dont need to refer to the other thread.


I tried all the above steps..still have the same error "device is activated but not in use"

---

### Post by niloferbano on 2010-09-29
> **xircon said:**
> If your wireless was working but now isn't try this:

[http://ubuntuforums.org/showthread.php?t=1584063](http://ubuntuforums.org/showthread.php?t=1584063)

look for my post.

Hi,

I still could not fix the issue.

---

### Post by brkearns on 2010-09-29
Your keyboard shortcut to disable the wireless networking might be turned on.  FN-F2 (looks like a little antenna).  Toggle that and check to see if the networking comes back up.

---

### Post by astrobob.tk on 2010-09-29
> **niloferbano said:**
> I tried all the above steps..still have the same error "device is activated but not in use"


I am sorry I couldnt help. I suggest you try the thread i linked if you havent yet & that you "bump" this thread as well for, so as others take notice of it & try to help.

P.S.: Make sure you mention what has been attempted to the moment if u consulted the other thread.

sorry again :(

---

### Post by niloferbano on 2010-09-30
> **astrobob.tk said:**
> I am sorry I couldnt help. I suggest you try the thread i linked if you havent yet & that you "bump" this thread as well for, so as others take notice of it & try to help.

P.S.: Make sure you mention what has been attempted to the moment if u consulted the other thread.

sorry again :(

:)..thats ok..I reinstalled ubuntu and it got fixed. But now i have one new problem. i was able to access windows share from ubuntu using smb://IPaddress/sharename..now its not working..

Please let me know if you know how to fix this

---

