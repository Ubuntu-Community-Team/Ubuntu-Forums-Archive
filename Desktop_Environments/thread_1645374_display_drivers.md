---
title: "display drivers"
date: 2010-12-14
forum: Desktop Environments
---

### Post by b1235762 on 2010-12-14
I got ubuntu 10.04. dont know wchich driver had previous. 
Tried get better quality in youtube, so I reinstal it to catalis ATI(with Synaptic). that was not good idea( I knew what I was doing in 50% <LOL>).
Now I got some problems with display. 
SMplayer "Unsuscpectly quit working. Code of exit 1".
 Cant zoom the screen with Win(one keyboard & scrool up)
In System>Preferences>Display I got "It seems that display driver dont operate needed addons to use this tool. Use tool from grafic card manufacturer?"
When I say YES i got Iniciation Error.aticonfig dont support my card.
When i say NO it opens Display Preferences.but Refresh Frequency cant be set-it shows 0Hz.
[html]komp@xxx:~$ lshw -c display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: RV350 AP [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32 mingnt=8
       resources: memory:c0000000-cfffffff(prefetchable) ioport:a000(size=256) memory:e9010000-e901ffff memory:e8000000-e801ffff(prefetchable)
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AP [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=32 mingnt=8
       resources: memory:d0000000-dfffffff(prefetchable) memory:e9000000-e900ffff

[/html]
How can I return to deafult display driver?

---

### Post by Krytarik on 2010-12-14
It seems you're using a similar card like my mum, ATI Radeon 9600.
Those belong to the so called "legacy" cards, ATI's term, altough just 5-years old.:mad:
ATI is no longer developing drivers for these cards, annoyingly, the old drivers don't support the current x-server. Thus, the drivers you have installed obviously are not build to support your specific video card.

Consequently ATI made the source code of their linux drivers available as open source, which is used to develop the so-called "nouveau"-drivers. These are the only enhanced drivers which are working currently with those legacy cards. The performance of those is significant higher than of the generic drivers, but still don't reach that of the old ATI-developed proprietary drivers.

Thus I recommend to remove the driver you just installed via Synaptic, and install the nouveau-drivers via "System -> Administration -> Additional Drivers".

---

### Post by b1235762 on 2010-12-16
*get mad and solved = re-installed the system:] 			*

---

### Post by gradinaruvasile on 2010-12-16
Lol. You had to only remove the driver and restart.

---

### Post by Krytarik on 2010-12-16
> **Krytarik said:**
> It seems you're using a similar card like my mum, ATI Radeon 9600.
Those belong to the so called "legacy" cards, ATI's term, altough just 5-years old.:mad:
ATI is no longer developing drivers for these cards, annoyingly, the old drivers don't support the current x-server. Thus, the drivers you have installed obviously are not build to support your specific video card.

Consequently ATI made the source code of their linux drivers available as open source, which is used to develop the so-called "nouveau"-drivers. These are the only enhanced drivers which are working currently with those legacy cards. The performance of those is significant higher than of the generic drivers, but still don't reach that of the old ATI-developed proprietary drivers.

Thus I recommend to remove the driver you just installed via Synaptic, and install the nouveau-drivers via "System -> Administration -> Additional Drivers".
The "Nouveau"-drivers are for Nvidia-cards, the open-source ATI-drivers are called "Open Source Edge", sorry.
And they can be installed this way: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers) , not the way mentioned above. (I have to check this at my mum's machine also.;))

---

