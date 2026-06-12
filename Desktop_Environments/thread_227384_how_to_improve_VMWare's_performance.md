---
title: "how to improve VMWare's performance?"
date: 2006-08-01
forum: Desktop Environments
---

### Post by pmark on 2006-08-01
I need to run a set of Windows programs that Wine doesn't currently run. So I either need to dual-boot or virtualize. I decided to give a test on the second choice.

After the recent anouncement that VMWare Server 1.0 was available for free (as in beer), I got tempted to test it.

My hardware is:

Chipset: NForce4
VGA: Nvidia 6800GT
CPU: Athlon64 3000, but I am running the 32-bit version of Ubuntu
RAM: 1GB

I thought that it would be better to install Win2000 since it's a more light-weight OS. The installation was doing fine but the mouse was lagging (periodically did not respond for small time intervals, a lag of 0.3sec every 1.5sec). I hoped that this would be fixed once I boot on Windows but it didn't change. So I started from scratch with WinXP. Same result.

Once I tried to install VGA drivers, I found out that Windows haven't found my graphics card for one. This seems strange since I have [installed the Nvidia drivers on Ubuntu](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29).

Maybe I chose the wrong version of VMWare. There is also VMWare Player, which although not designed to create an "image", can be "[hacked](http://homepage.sunrise.ch/mysunrise/ekeller00/EricKellerUbuntuPage.html)" or [tricked](http://www.easyvmx.com/) to do so.

Any ideas on how to get a decent performance?

---

### Post by rejser on 2006-08-01
I run vmware to set everything up and then run it through vmware-player. Real difference in performance.
Win won't find your graphics card I belive., just run the default. (you should be able to set high resolution at least)

---

### Post by evil_elman on 2006-08-01
There should be something 'VMWare tools' (can't remember exact name) which fixes the laggy mouse especially.

I've used VMWare Server (the beta) without any problems but you need to remember that the computer that VMWare is emulating also has its own graphics card. The drivers for this card is included in the above 'VMWare tools' package.

If my memory serves me right, there should be a notification at the bottom of the VMWare console stating that the tools haven't been installed. There should also be an option to install these in the regular VMWare console menus (at the top).

A good idea is also to allocate VMWare Server more RAM than default. Since you've got 1GB RAM I would suggest close to half of it for VMWare Server and the rest for Ubuntu.

Don't virtualize a Windows installation hoping that 3D, video playback or anything similar will run smoothly, though.

---

### Post by rejser on 2006-08-01
To install vmware tools.
Start win. ctrl+alt. vm-menu, install vm-tools

---

### Post by pmark on 2006-08-03
Thank you for your replies.

Unfortunatelly the hack to install WinXP using just the VMWare player didn't work. Moreover, it seems that I can't have both, VMPlayer and VMWare server, installed at the same time. So I kept only VMWare server.

Installing the VMWare Tools did the job!

The main purpose that I want to run VMWare is Sony Vegas. I am trying to make Cinelerra work on Ubuntu but so far I am out of luck.

---

