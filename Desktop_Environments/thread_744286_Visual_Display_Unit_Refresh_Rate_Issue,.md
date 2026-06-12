---
title: "Visual Display Unit Refresh Rate Issue,"
date: 2008-04-03
forum: Desktop Environments
---

### Post by king909 on 2008-04-03
Hello everybody, I've swiched from WINXP to UBUNTU 7.10, I own a AL718 ACER TFT Monitor, In the windows OS i was able to set the refresh rate to 70hz without problems, I have a nvidia 5200 PCI FX GPU. In the ubuntu tool which is called screen and graphics it detects my VDU as a PLUG AND PLAY, when i go down and manually look for screns I cannot find the AL718 in the model option. closest match was AL702, can somebody help me out here, because I'm stuck at 50hz and its bad for my eyes.:(

thanks

---

### Post by prshah on 2008-04-03
> **king909 said:**
>  In the windows OS i was able to set the refresh rate to 70hz without I'm stuck at 50hz and its bad for my eyes.:(
thanks

Open a terminal, give the command ```
sudo dpkg-reconfigure xserver-xorg
```, then go through all the options until you get to monitor; there, choose "advanced", then set the custom refresh rates and resolutions that you want.

HTH

---

### Post by king909 on 2008-04-03
well when i enter this, it reconises my on board intel springdale GPU.. xD
I dont get a choice to pick the NVIDIA.. xDwhat now?

---

### Post by prshah on 2008-04-06
> **king909 said:**
> well when i enter this, it reconises my on board intel springdale GPU.. xD
I dont get a choice to pick the NVIDIA.. xDwhat now?

If you have onboard video (and it looks like you do), go to the BIOS and disable it first, then go through the "sudo dpkg-rec..." process again.

---

