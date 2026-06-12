---
title: "[SOLVED] Dell-buntu?"
date: 2008-01-28
forum: Dell  Ubuntu Support
---

### Post by slughappy1 on 2008-01-28
I just bought new Dell (Inspiron 1420) that came with Ubuntu pre-loaded on it. I plan on re-installing st so that I can encrypt my hdd. When I boot it up normally and check the restricted drivers there are 2 objects in use : 

1) Conexant modem engine
2) Intel(R) PRO/Wireless 3945 Network Connection driver for Linux

And then when I boot up the Live CD there is on the Intel driver in the restrivected driver list. My question is, what is the Conexant modem engine and when I re-install Ubutnu will it install it. Do I need it?

---

### Post by Ub1476 on 2008-01-28
I have Intel 3945 as well, and when Ubuntu has installed, it will notify you about its drivers which is available in the restricted driver manager. I don't know what **Conexant modem engine** is, but if Dell has installed it, I guess you should as well (it obviously has something to do with internet in a way or another).

---

### Post by fragos on 2008-01-28
I believe the Conexant modem engine is for the built in telphone dial up modem.

---

### Post by Chasoid on 2008-01-29
Correct ... it's for the (telephone) modem.

If you're not going to do any "dial-up" operations, you don't need it.

I reloaded my Dell E1505N with the Ubuntu .iso and it works fine.  The only thing I'm missing from the Dell version of Ubuntu is that I think their "mouse settings" program has an option to control settings for the touchpad.  My touchpad works to my liking, so I don't miss that functionality.

---

### Post by fragos on 2008-01-29
The Dell 7.10 iso dose have touchpad tab on mouse settings.  The tab has minimal settings to enable/disable taps and for vertical/horizontal scrolling.  Disabling of tabs and allowing vertical scrolling works, enabling horizontal scrolling on my 1420n did nothing.

---

### Post by jdelaros1 on 2008-01-29
The Conexant modem engine appears in Restricted Drivers because it uses a proprietary driver from Conexant. This driver is not included in the Ubuntu LiveCD from ubuntu.com, Dell added it to their image to make the modem work. If you wipe out your original Dell image, you can retrieve the modem driver from  [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver).

---

