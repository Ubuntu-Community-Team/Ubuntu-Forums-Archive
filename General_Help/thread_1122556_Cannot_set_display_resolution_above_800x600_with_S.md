---
title: "Cannot set display resolution above 800x600 with SiS graphics"
date: 2009-04-11
forum: General Help
---

### Post by Guy_AD on 2009-04-11
At the moment I'm fixing my mum's friend's laptop which had a severe case of Windows-itis. So I installed Ubuntu 9.04 instead, and got all the drivers up and running. Everything is working fine except the fact that I can't set the screen resolution higher than 800x600, which is a bummer because the display is 1280x800. I tried adding the following to /etc/X11/xorg.conf:
> 
        SubSection "Display"
                Modes    "1280x800"
        EndSubSection

to absolutely no avail. The results of "lspci -v |grep VGA" were:

> 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


I have checked that the SiS driver is installed correctly in Synaptic Package Manager (which it is), does anyone know why I can't set the resolution any higher? I know SiS is not the most Linux friendly company in the world, so does anyone have a workaround?

Thanks in advance

---

### Post by Catsmeat on 2009-04-13
The default SiS drivers don't work with this chipset. Luckily there are alternative drivers available. Check out this thread:

[http://ubuntuforums.org/showthread.php?t=958967&page=12](http://ubuntuforums.org/showthread.php?t=958967&page=12)

---

