---
title: "Extend dual monitor"
date: 2010-11-11
forum: Desktop Environments
---

### Post by Ambiorix3 on 2010-11-11
Hey everyone,

this is a topic that has been covered a numerous of times already but i didn't find my answer so here i am. Before we begin, let me just say i've using ubuntu since a couple of weeks. I'm learning a lot but i'm still a newbie at the moment.

To save some time, let me give you my specs:

Distribution: Ubuntu 10.10 x64

Graphics card: ATI Radeon HD 4890
Graphics driver: ATI proprietary FGLRX graphics driver

Monitor 1: Samsung syncmaster 2494HS (24")
Monitor 2: Acer x223w (22")

My graphics card has 2 entrances. 1 DVI entrance and 1 HDMI. 
The Samsung monitor is connected with a dvi-cable through a dvi-hdmi connector.
The Acer monitor is connected with a vga-cable through a vga-dvi connector. 

The thing is, when i plugged in my second monitor (the Acer), it got picture immediately. Unfortunately, it's a mirror image of my Samsung monitor. So i opened the settings in system => preferences => monitors and unchecked "Same image in all monitors". It told me to log off and log back in. I did, but it didn't change. 

Then i discovered the Ati Control panel. In the Multidisplay section i set the settings to extend. I had to reboot, i did and it didn't change anything. The settings revert to what is was before. I must say that in the "Display options" screen, it sais "You currently have only one desktop enabled. Configuring more than one desktop in the Display Manager will allow you to configure Xinerama". But like i said, everytime when i enabled 2 desktops, i have to reboot and everything is reset.

I read multiple tutorials about configuring xorg.conf but i have no idea where to begin.

Can you help me?

---

### Post by Ambiorix3 on 2010-11-11
[SOLVED]

Never mind. All of a sudden, it worked. I just rebooted and strangely got my login screen on the second monitor but after logging in, i got the Samsung as main monitor and Acer monitor as extended.

---

