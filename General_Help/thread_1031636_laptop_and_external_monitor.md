---
title: "laptop and external monitor"
date: 2009-01-05
forum: General Help
---

### Post by richardy on 2009-01-05
Hi,
Have recently installed xubuntu 8.10 onto a asus Z91L laptop and everything is working fine however i have a query regarding running an external monitor from the laptop (can do this under windows). I have the utility program xrandr to run the external monitor and this works but it only gives a maximum resolution of 1024x768 (max laptop resolution) as opposed to the monitor (philips 170s LCD) resolution of 1280x1024. I know the laptop can supply this resolution since when i run windows it automatically sets the correct monitor resolution when i switch from laptop to external monitor.

Is there a way of getting the external monitor to operate at the correct resolution when running xubuntu?

Any help would be much appreciated.

Cheers.

---

### Post by loboc on 2009-01-05
what kind of video card is it 

the Nvidia proprietary (restricted)  drivers have dual support availible from the system prefs

I think the ATI proprietary driver is a little more obtuse,  you may have to edit xorg.cong in /etc/X11 
but it may be better i have not used an ati card in a while

---

### Post by richardy on 2009-01-07
Hi,
Thanks for the reply. As far as i can work out the graphics chipset is intel.

I am not in xubuntu at the moment but i dont remember any dual monitor support in system preferences but i will double check.

Cheers.

---

