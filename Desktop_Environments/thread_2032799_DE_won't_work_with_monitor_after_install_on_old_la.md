---
title: "DE won't work with monitor after install on old laptop"
date: 2012-07-24
forum: Desktop Environments
---

### Post by rollingthunderb on 2012-07-24
Greetings,

I am having trouble seeing any desktop after clean install. I'm not an expert (more of a noob than anything), but I've tried doing my reading and work on this as best I could. I'm hoping someone out there can help. Thanks in advance.

Big Picture:
Monitor will show "splash screen" of whatever distro I choose (Xbuntu, Lubuntu or Ubuntu), but after the nice little spalsh it trys to display the login screen, but the monitor craps out.

Why am I using a monitor instead of the laptop screen?
 I have to use the monitor as the screen on the laptop is busted. 

Specs:
Machine = Dell C600 laptop. 512Ram 20GigHD.
I am using the docking station for the laptop, but the system is configured to use system video card.
Monitor is old Relisys CRT.

Distros tried and successfully installed:
Xubuntu 12.04 Alt i386
Lubuntu 12.04 Alt i386
Ubuntu   10.04 Alt i386 - Was trying to see if the legacy LTS would work.

With all of these I can ^F1 to CLI and login, and even complete updates. 

I have tried modifying grub (sudo nano grub) with the following after quiet splash;
xforcevesa, nomodeset, radeon.modeset=0 & radeon.modeset=1. 
None of the them improve my situation.
Yes, I do sudo update-grub after each try. 

Is there something else I could try? Maybe force it to work with another parameter I'm not familiar with beyond xforcevesa?

I suspect someone will ask for my lspci output, but I'm not familiar with how to get that in here since I can't get to a GUI. If you really want it, I'll take a picture. or copy it manually I guess.

Thank you for reading.

---

