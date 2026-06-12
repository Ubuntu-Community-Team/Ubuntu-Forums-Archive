---
title: "Mini 9 8.04, two issues..."
date: 2009-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-06-23
I have a Dell mini 9 running Dell's custom 8.04. I currently have two problems with it, not major, but very annoying.

First issue, and most important, my wireless. My wireless functions fine, but the problem is, when I boot up the laptop, the driver is not in use. My networkmanager says "no wireless networks found". If I open up System>Admin>Hardware Drivers it shows my Broadcom STA driver. It says it is enabled but not in use. If I click disable and then re-enable it, it says it is in use. After that, my wireless works... Until I reboot or shutdown that is, then I have to go through it all again.

Second issue, for some reason, the "minimize", "maximize" and "exit" buttons in the top right of any and all applications is gone, unless I right click on the program in the task-bar and minimize it. Then they appear. But if I maximize it, they disappear again.

These are my only two issues. If anyone has any insight as  to how to fix these, I would be most appreciative. Thanks in advance :-)

---

### Post by ugm6hr on 2009-06-24
I am now on 9.04.

But I never saw either of these problems on the original Dell 8.04, which I used daily for over 3 months.

Not certain what could cause these: perhaps Dell's updates have caused problems; or your home directory is corrupted (i.e. Gnome settings etc).

---

### Post by Arndtwe on 2009-06-24
I have been using the Dell custom kernel for around 7 months almost daily, and I have not had these (or any other) problems before. They were not caused by an update. I was in synaptic removing different bluetooth applications at the time these came about. If they are related I have no clue. Not sure why removing different bluetooth programs would do this.

Any suggestions?

---

### Post by Arndtwe on 2009-06-24
Anyone?

---

### Post by buzzware on 2009-06-25
Well, the second issue sounds like Maximus.  You can go into the Gnome config editor and find Maximus then clear the "undecorate" check box.

I had issues with wireless initially that were corrected after some updates, but I can't say now since I have moved to 9.04 UNR.

Good luck!

---

### Post by anjilslaire on 2009-06-25
I've been running 8.10 UNR and 9.04UNR exclusively on mine, and the broadcom wireless card started acting up a while back, randomly appearing, disappearing, losing connectivity even when it reported full signal strength, etc.

I finally just replaced the wireless card withe an Intel 3945a/b/g Mini PCI card from Amazon for less than $30. No restricted drivers needed, no more problems.

---

### Post by Arndtwe on 2009-06-25
Thanks for the replies guys! I got maximus fixed... I now have my buttons back. And that wireless card looks like a good idea. You put that card into a Dell mini 9, correct? Was this difficult? Could you provide instructions, or, point me to some?

---

### Post by anjilslaire on 2009-06-27
Yes, a Mini 9. Unscrew teh bottom plate frpm the Mini, and you'll see the wifi card held down by 2 screws, and with 2 wired antennae leads connected. 

1. Power off the Mini, and remove the battery.
2. Gently lift the leads straight up off of the connectors; they'll sort of pop off.
3. Unscrew the 2 screws holding the wifi card in place. It is stamped Broadcom on it, and will pop out at an angle and slide off easily. 
4. Replace it with a new card, it will only fit it one-way.
5. Pop the antennae leads back in place securely, and put the lid back onto the Mini.

Power up :)
Oh, before I shut down I disabled the Broadcom driver in the Restricted Drivers.

Here's a guide:
[http://www.ubuntumini.com/2008/09/dell-inspiron-mini-9-service-manual.html](http://www.ubuntumini.com/2008/09/dell-inspiron-mini-9-service-manual.html)

The card I installed is:
[http://www.amazon.com/gp/product/B000EDQOK8/](http://www.amazon.com/gp/product/B000EDQOK8/)

---

