---
title: "Installed nvidia-glx and but nvidia-settings gives me errors"
date: 2007-06-03
forum: Desktop Environments
---

### Post by runesvend on 2007-06-03
Wanting to utilize my nVidia graphics card (GeForce FX 5200) I installed the nvidia-glx package in Synaptic. After doing this and restarting my computer I ran *nvidia-settings* and got the following response in the terminal:

> rune@rune-desktop:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

I've included my xorg.conf configuration file and the log created by running the command "*sudo nvidia-bug-report.sh*" (nvidia-bug-report.log).

*lspci | grep -i nvidia* gives the following output:

> 
rune@rune-desktop:~/Desktop$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

Thanks for your input.

---

### Post by runesvend on 2007-06-03
I used Feisty's "Restriced Drivers Manger" and now it works perfectly. Sorry for bothering you guys. Have a good day :).

---

