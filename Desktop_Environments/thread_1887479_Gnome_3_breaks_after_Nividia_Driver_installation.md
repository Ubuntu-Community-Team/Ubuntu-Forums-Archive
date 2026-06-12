---
title: "Gnome 3 breaks after Nividia Driver installation"
date: 2011-11-27
forum: Desktop Environments
---

### Post by bhupinderjitbawa on 2011-11-27
I have installed ubuntu 11.10(tried mint 11 too even mint 12). It comes with unity which i dont like, so i install gnome 3. 

**Problem**
---------------------------
*If i install my nvidia drivers from additional drivers, it breaks the gnome 3 and automatically converts it into "broken classic gnome 2" with only "applications and places menu" and gnome 3 get lost.*

----------------------------
*If i dont install nvidia drivers, laptop heats up and it hang after few hours and after restart gnome 3 get lost and "broken classic gnome 2" comes.*


**I have tried ubuntu and mint my favourites. so should i drop the idea of using gnome 3 or there is any solution i should try??**
attached the snapshots(same things happen to ubuntu) of before and after installation of nvidia drivers.

---

### Post by kensum on 2011-11-27
Your mint12 screenshot is correct. Gnome3 with the msge extentions enabled. The next shot is the fallback mode screen for gnome3. I appears that your nvidia drivers are not working in ubuntu. Go to your hardware drivers  and see what is recommended and what is enabled. If is works in mint, it should work in ubuntu. Is this a notebook with an apu cpu. On startup it will use the intel gpu drivers and be correct. When you install the nvidia drivers they will not work correctly and will not allow the intel drivers to work. IF this is the case, i believe it is called optimus video, you will need to run the intel drivers for now.

---

