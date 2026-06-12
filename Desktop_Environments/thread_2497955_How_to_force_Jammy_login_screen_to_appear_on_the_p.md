---
title: "How to force Jammy login screen to appear on the primary monitor"
date: 2024-05-23
forum: Desktop Environments
---

### Post by goodstuff9 on 2024-05-23
ubuntu 22.04.4, gnome 42.9, Wayland


In the Ubuntu/gnome settings, I have five monitors, monitor #1 is set as the primary monitor.  


I have verified that in ~/.config/monitors.xml that monitor #1 is set as primary.  


I have verified that /var/lib/gdm3/.config/monitors.xml exactly matches what is in ~/.config/monitors.xml, and that the ownership of the /var/lib/gdm3/.config/monitors.xml file is gdm:gdm.  


Everytime I start up the computer, the initial Ubuntu login screen appears on monitor #5.  How do I make it appear on monitor #1?

---

### Post by MAFoElffen on 2024-05-25
There is a difference in the primary display in BIOS, and the primary display in a Desktop user session, where 'you' set that in the user session... To change the primary display in BIOS, where it boots from for post, and the OS early boot, where the splash screen comes up in...

Change the display cable order in how it is connected. I know this may not work, as you may have different interface types, that connect between... But that is how that is done for before the user session gets config'ed.

Just saying...

---

### Post by goodstuff9 on 2024-05-26
> **MAFoElffen said:**
> There is a difference in the primary display in BIOS, and the primary display in a Desktop user session, where 'you' set that in the user session... To change the primary display in BIOS, where it boots from for post, and the OS early boot, where the splash screen comes up in...

Change the display cable order in how it is connected. I know this may not work, as you may have different interface types, that connect between... But that is how that is done for before the user session gets config'ed.

Just saying...


Thank you.  

Sorry, but now I have to ask you a different question:  How does one "change the display cable order"?  I can't find that setting anywhere that I look.

---

### Post by MAFoElffen on 2024-05-28
It is "set" - hardwired, It is what it is and the port order cannot be changed.

I think I remember the older nVidia GPU cards that has the same ports all the same type as it being the closest port to the top of the case is port-0, and they go from there. But that with cards with mixed type ports on the same card, that it can be by type during BIOS boot.

My recommend, is that you are there and can see which port is connected to which port-cable-display. Which ever display shows the POST and Plymouth Splash is port-0 in priority. Change that display end of the cable to whatever display you want that on. Go from there.

---

