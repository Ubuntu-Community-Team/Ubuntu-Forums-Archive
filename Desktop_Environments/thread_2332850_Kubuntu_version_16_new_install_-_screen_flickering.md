---
title: "Kubuntu version 16 new install - screen flickering using Firefox on Nvidia gr. card"
date: 2016-08-04
forum: Desktop Environments
---

### Post by richlion2 on 2016-08-04
Hello,

I have an HP laptop with this graphics card:
NVIDIA Corporation G84GLM [Quadro FX 570M] (rev a1)

I had Kubuntu 15 and I used one of the recommended drivers that was on a list of drivers in the System Settings -> Additional Drivers. No problems after upgrading another Acer laptop to Kubuntu 16.
However, on this HP laptop I had to make a clean Kubuntu 16 install. In the System settings there are no additional drivers.
I have a problem with a flickering screen, especially using browsers, Firefox and Chromium seem to be affected. Is this something that can be fixed without installing Nvidia drivers?
If I have to install nvidia drivers, how do I install a recommended driver from the Ubuntu repository? Name, version?

Regards,
Rich

---

### Post by QIII on 2016-08-04
Please clarify:

16.04 or 16.10?

---

### Post by grahammechanical on 2016-08-05
Connected to the internet? Allow time for the utility to find the drivers?

For those who do not know, in Ubuntu 16.04 there are no AMD proprietary video drivers because AMD have not upgraded their proprietary video drivers to use the x server version in 16.04. That is not relevant in this particular situation.

When installing Ubuntu 16.04 (making an assumption that "16" is 16.04) on the HP did you tick the box "Install third party software?" That would have installed an Nvidia proprietary video driver.

Open System Settings>Details and see what it lists under Graphics. If it says Gallium 0.4 then the HP is running on the open source video driver Nouveau. If it says llvmpipe then a fallback open source video driver is being used because of some conflict with the proprietary video drivers. If it says something else, then that would indicate that an Nvidia driver is installed.

EDIT: Oh, you are on Kubuntu. Well, look for something that will give information about the OS to find out what video driver is being used.

Regards

---

### Post by richlion2 on 2016-08-05
Hello, 
this is the version I have:
[FONT=monospace][COLOR=#000000]rysio@rysio-HP-Compaq-8510w:~$ lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial


[/FONT]> 
[COLOR=#000000]did you tick the box "Install third party software?"[/COLOR][FONT=monospace]
[/FONT][FONT=monospace]

Yes, I did. Checked in Muon in the Graphics section, can't find things like [/FONT][COLOR=#000000]Gallium  nor [/COLOR][COLOR=#000000]llvmpipe.

When going to Settings -> Additional Drivers, still nothing, empty screen and I am connected to the Internet.

I just had some updates, so I'll reboot the check the Additional Drivers again. 

Thankss Guys



[/COLOR]

---

### Post by richlion2 on 2016-08-08
Hi All, 

I have not installed any Nvidia drivers, I also still cannot find anything in the Additional Drivers in System Settings. However everything seems to be working fine now, I think maybe another non-browser application is causing this issue. Can I ask what is the difference between version 16.04 and 16.10?

---

