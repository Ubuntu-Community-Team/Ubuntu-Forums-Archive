---
title: "Help with Keyboard and pointing devices"
date: 2010-07-18
forum: Desktop Environments
---

### Post by buddiemac on 2010-07-18
I am running UBUNTU 10.04 on an X86 system 64bit. I am trying install  a wireless keyboard and am not having much luck.

-My non wirelessUSB keyboard and mouse work fine.
-My wireless logictech mouse works fine without adding any special drivers/packages
-Wireless Keyboard (LX500, uses same receiver as mouse) does not work with standard config
-Adding HIDPOINT and selecting my wireless mouse and keyboard (LX500) - wireless key board does not work. Mouse still works.

Since my wireless mouse worked before HIPOINT installation (64 bit), I believe HIDPOINT is not working.

HIPOINT Does not detect my wireless devices auto, must manually select them. So I believe that there is some conflict with other drivers.

Can anyone point be in a direction to look? What are the typical configuation files and drivers used to configure standard USB mouse and keyboards? What are some other software that might be installed that is conflicting with HIDPOINT? Thanks.

---

### Post by buddiemac on 2010-07-23
I think I have this one solved. The LX500 has a secure mode where the scan codes are encrypted. 

So to get the keyboard working one is required to take the keyboard out of secure mode. This is done by:

CTRL-ALT-F12

Then re-pair your keyboard to your receiver.

I do not believe that secure mode is supported in Linux.:p

---

