---
title: "Inspiron 6000 battery problem in Ubuntu 9.10"
date: 2010-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by generate on 2010-02-26
I have recently installed 9.10 on an old Inspiron 6000 laptop (as an Ubuntu only install on a new replacement hard drive).

I now find that although Ubuntu seems to recognise the battery (there is an icon and it displays % charged), whenever I disconnect the power cord the laptop just dies as if there is no battery in at all.

It is a fairly new replacement battery, but used to work fine under Windows XP, so I'm assuming it is an operating system issue.

I have searched the threads here and got as far as finding the info file, but am very new to Ubuntu so now need further advice, please.

Thanks in advance for any help.

 cat /proc/acpi/battery/BAT0/info   present:                 yes  
 design capacity:         6600 mAh  
 last full capacity:      6600 mAh  
 battery technology:      rechargeable  
 design voltage:          11100 mV  
 design capacity warning: 660 mAh  
 design capacity low:     200 mAh  
 capacity granularity 1:  66 mAh  
 capacity granularity 2:  66 mAh  
 model number:            DELL 00  
 serial number:           2413  
 battery type:            LION  
 OEM info:                Sony

---

### Post by coffeeaddict22 on 2010-02-27
Hi,
There's a whole lot of changes coming to Power management because HAL is on its way out and Device Kit is coming.  I'm not much of a power guy, but there's a few things you could look at.  When you right click on the battery icon, in the power history what does it look like the battery is doing?
I've gone through a couple of laptops at least now- the combination of children and power cord usually means the connector gets snapped at some point, and you may not be able to charge.

---

### Post by generate on 2010-02-27
Hi,

Thanks for the reply.

Looking at the battery history over the past week, it always shows 99% charged.

The problem isn't that it won't charge, but that the laptop doesn't draw power from it when the power cord is unplugged.

Whenever I disconnect the power cord the laptop just dies as if there is  no battery in at all.

Any ideas?

---

### Post by coffeeaddict22 on 2010-02-27
Had a look at [this page on the Dell website?]("http://ftp1.us.dell.com/diags/R66243.htm") 

Do the dumb stuff first.  I assume you've checked the battery contacts, made sure there's no dead flies on the motherboard, that sort of stuff.

---

### Post by generate on 2010-03-01
Hi and thanks again for the response.

I've done all the basic checks you mention, and reviewed a lot of threads and help pages about batteries not charging ... but nothing seems relevant to this problem ...

Just to repeat, the battery seems to be present and charging, but when I disconnect the power cord the laptop just dies as if there isn't a battery present at all.

Any further suggestions appreciated!

Thanks ....

---

### Post by coffeeaddict22 on 2010-03-01
For a bit more info, you could try running the following command: ```
 devkit-power --monitor-detail

```
and see what it reports, especially when you pop the battery out of it's bay and put it back in again.

Just a thought; have a look in your power management options (System/Preferences/Power Management) and see if there's anything set in there to shut your machine off when it goes onto battery.  It might be worth looking in the BIOS too.

---

### Post by frank0936 on 2011-01-18
My Inspiron 8200 does the same thing on two different power cords. I've only had it plugged in and it says the battery is only 30% charged. The battery was new a couple of months ago. On the previous version of Ubuntu it would tell me the battery was charging. Now it doesn't do anything.

---

### Post by frank0936 on 2011-01-18
My Inspiron 8200 does the same thing on two different power cords. I've only had it plugged in and it says the battery is only 30% charged. The battery was new a couple of months ago. On the previous version of Ubuntu it would tell me the battery was charging. Now it doesn't do anything. When I tried to post this it told me I had to wait 20 seconds between posts and this is my first post of the day! Oh, and I'm on Ubuntu 10.04.

---

### Post by frank0936 on 2011-12-03
There are too many battery questions about batteries not charging with too many different laptops for this to be hardware issue. This is an OS issue, but no one seems to want to acknowledge it.

---

