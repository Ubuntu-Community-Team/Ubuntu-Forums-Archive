---
title: "kde how to hibernate on laptop lid close"
date: 2009-11-08
forum: Desktop Environments
---

### Post by christoforever on 2009-11-08
I can't figure out for the life of me how to make kde hibernate when the laptop lid is closed. I can't find the option anywhere. What am I missing?

---

### Post by Untitled_No4 on 2009-11-09
Kmenu -> Settings -> System Settings
Change to Advanced tab
Click on Power Management (light bulb icon)
Click Edit Profiles

And the setting's there.

---

### Post by Operan on 2009-11-09
This function still does not work properly in Kubuntu 9.10. Sometimes it hibernates, sometimes it logs out, sometimes it locks screen and sometimes it does nothing. :|
PS: I edited all power profiles so that my laptop hibernates when the lid is closed. Sometimes it works fine, sometimes not.

---

### Post by ChrischanM on 2009-11-09
> **Operan said:**
> This function still does not work properly in Kubuntu 9.10. Sometimes it hibernates, sometimes it logs out, sometimes it locks screen and sometimes it does nothing. :|

Could this problem be related to different power management profiles? With a LMC (left mouse click) on the battery status you can see the current profile and also change it: More... -> Edit Profiles -> Actions. There you can select for every profile the outcome of several buttons or if you close the laptop. The instruction is related to Kubuntu 9.10.

It can also be related to another problem. A while ago STD and STR worked, but now unfortunately this time is over.

---

### Post by Operan on 2009-11-09
PS: I edited all power profiles so that my laptop hibernates when the lid is closed. 

**I found another problem**: When I click Suspend to Disk, the screen get black with only cursor in few seconds, and after that, my laptop returns to the state before I click Suspend to Disk, and I can continue my work. OMG, it's funny!:lolflag:

---

### Post by mrboojive on 2009-11-10
> **Operan said:**
> **I found another problem**: When I click Suspend to Disk, the screen get black with only cursor in few seconds, and after that, my laptop returns to the state before I click Suspend to Disk, and I can continue my work. OMG, it's funny!:lolflag:

Do you have a swap partition? Ubuntu can't hibernate without a swap partition and that sounds like what happens when you try to.

---

### Post by christoforever on 2009-12-01
Untitled_NO4 ... thanks for pointing me in the right direction. I honestly have no idea how I missed looking there ( maybe because I'm still a KDE noob? ) but that did it for me. Sorry it's taken so long to get back, I've just been busy at work. But thanks.

---

### Post by COKEDUDE on 2011-06-07
> **Untitled_No4 said:**
> Kmenu -> Settings -> System Settings
Change to Advanced tab
Click on Power Management (light bulb icon)
Click Edit Profiles

And the setting's there.

Thank you. I couldn't find it.

---

