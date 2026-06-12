---
title: "Intel NUC7 either no video or no sound"
date: 2018-09-24
forum: Desktop Environments
---

### Post by jensk on 2018-09-24
I have bought a NUC7PJYH with UHD605 graphics because our new 50" UHD tv was to big a mouthfull for my old Acer Revo 3700 Nvidia ION as a Mythtv frontend.
I installed Xubuntu 18.04 and Mythtv-frontend on the NUC and connected the TV via HDMI-1. 
1,st error was, when I boot the NUC the tv says no input at the HDMI port. If I pull out the HDMI and plug it in again, I get the desktop. 

I startet out trying to fix the missing desktop by setting the "nomodeset" ind the grub boot. It corrected the missing desktop but when nomodeset i set in GRUB I have no sound through HDMI.  Pavucontrol states that there is a HDMI output but it is unplugged eben though it is plugged in.
 
If I remove the nomodeset parameter in grub i have sound over HDMI but I need to unplug and replug the HDMI after every boot to get a desktop on the TV.

What parameter do I need to set in grub to have both picture and sound. Any good suggestions?

---

### Post by jensk on 2018-10-15
I have found the solution - it was a kernel error that caused the formware not to load:
[https://askubuntu.com/questions/1079310/nuc7-either-no-sound-or-no-video/1083866#1083866](https://askubuntu.com/questions/1079310/nuc7-either-no-sound-or-no-video/1083866#1083866)

---

