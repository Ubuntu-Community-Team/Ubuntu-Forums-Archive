---
title: "wireless network"
date: 2005-12-15
forum: Desktop Environments
---

### Post by arkface on 2005-12-15
hi,

i have a hp pavilion dv4000 and im trying to get the wireless internet to work. it works fine on windows. im actually installing the base system as i type this on another computer. 

i tried to get my network setup in the installation process, but it failed. 

as i am not linux savy, i need you all to go easy on me

scott

---

### Post by Lambert on 2005-12-15
Wireless during setup doesn't work well. Not sure if anybody has gotten it set up during install.

Looks like your laptop will have the centrino wireless intel pro wireless 2200bg which uses the ipw2200 driver. This driver is part of breezy. So after you install just go to system>administration>networking

if you card is in the list then there is probably a working driver loaded, just set the properties for the device and then try to activate.

If you're using wpa encryption there are more steps necessary then this.

If you can't get connected you can go to the wirelesstroubleshootingguide in my signature. walk through the steps and if you get stuck post more detail including output of commands related to the section you're stuck at.

---

### Post by alamba on 2005-12-16
Buddy I did talk about this in another thread yesterday, do a search...the HP DVXXXX series has a hard button on the top with wireless written on it. Press on it 2 times for the blue wireless light to come on.

I have the DV 1375 series laptop and once you activate wireless by pressing the button everything goes smooth.

Assuming u've now installed ubuntu...go to system>>admin>>networking...click on the wireless network card and click on activate...then press that button till the light comes on. You should be all set.

Akshay

---

