---
title: "Desktop Effects Problem"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by ditikos on 2007-04-23
I've did a clean install on ubuntu feisty. My card is Geforce 2 MX 400, so when the reboot (postinstall) occured it said that I had no screens (due to the nvidia legacy thing).

At the time the only viable solution to bootup my desktop was to install nvidia's 9631 Legacy drivers (the only ones that can enable argb and composite). Did it, rebooted on my new desktop. I enabled desktop effects and it was good.

I disabled desktop effects and then I used automatix to install newest nvidia drivers (so that I could go into restricted drivers menu). They changed the nvidia config program (although it said that the driver they were going to install was the same). When I rebooted and tried to enable desktop effects again there was a message "desktop effects cannot be enabled". But the funny thing is that when it showed it enabled it for 2-3 secs and then it reverted back to normal desktop. 

Running compiz normally from command line works ok. But I want to have the desktop functionality as well. Is there a way to restore desktop-effects?

---

### Post by orange2k on 2007-04-23
> **ditikos said:**
> I've did a clean install on ubuntu feisty. My card is Geforce 2 MX 400, so when the reboot (postinstall) occured it said that I had no screens (due to the nvidia legacy thing).

At the time the only viable solution to bootup my desktop was to install nvidia's 9631 Legacy drivers (the only ones that can enable argb and composite). Did it, rebooted on my new desktop. I enabled desktop effects and it was good.

I disabled desktop effects and then I used automatix to install newest nvidia drivers (so that I could go into restricted drivers menu). They changed the nvidia config program (although it said that the driver they were going to install was the same). When I rebooted and tried to enable desktop effects again there was a message "desktop effects cannot be enabled". But the funny thing is that when it showed it enabled it for 2-3 secs and then it reverted back to normal desktop. 

Running compiz normally from command line works ok. But I want to have the desktop functionality as well. Is there a way to restore desktop-effects?


There is no need to install the nvidia drivers with automatix, they are available in the restricted driver manager by default, so maybe thats the problem, but Im not sure if your MX 400 can handle the effects (it has only 32MB RAM I think)...

---

### Post by ditikos on 2007-04-23
The graphics are handled nicely with this card, both on beryl and compiz. The problem is on the desktop effects program, that apparently gets wrong readings about something.

If you run compiz/beryl on it's own it works smoothly and fine.

---

