---
title: "Gnome3 and Cinnamon suddenly only start in Gnome Fallback!"
date: 2012-05-28
forum: Desktop Environments
---

### Post by Superpelican12 on 2012-05-28
Yesterday I installed Bumblebee (only for bbswitch) in hope to be able to turn off my discrete Nvidia card (which I really don't need on Linux). It seemed to work as my estimated batterylife increase by half an hour. Everything was as normal. But this morning when I booted my computer and wanted to login to Cinnamon it send me to the Gnome Fallback mode! While yesterday everything just worked. When I select  "Gnome" it also boots Gnome Fallback. I have tried to turn on the Nvidia card again with "tee /proc/..... <<< ON". And logged out and logged in again, but that didn't seem to help either. So I uninstalled Bumblebee and BBswitch-dkms. And rebooted the computer (I have rebooted the computer several times now this morning) but everything kept the same.

What' s wrong? I want to restore my system just like it was before I touched Bumblebee/bbswitch. Gnome Fallback isn't that bad, but I want to try Gnome Shell again and prefer Cinnamon (which I installed via a Cinnamon for Ubuntu ppa).

Computer specs:
Core i3 2310M @ 2.1 GHz with Intel GMA HDblahablah
Nvidia GT520M (512 MB graphics memory)
4 GB RAM
Ubuntu 12.04

I think my onboard Intel GMA + Corei3 would be powerful enough to run Gnome3/Cinnamon if it can run Windows Aero. Plus it ran Cinnamon/Gnome3 before without any problems (effects included!).

EDIT: I have checked my System' s details in System Settings > Details > Graphics and where it first said "Driver: Intel Sandybridge Mobile" &  "Experience:  Standard" in Cinnamon,  it now says (in Gnome Fallback)"Driver: <empty>"/"Driver:      "  & "Experience: Fallback". I have the feeling that Bumblebee has messed up my drivers. And the Sandybridge Graphics driver isn't loaded anymore. But I don't know how to fix it, to check if the driver is loaded and how to manually load the driver.

---

### Post by arazour on 2012-06-05
I've got the same problem here on Vostro 3350 with Radeon HD 6400M graphics

---

### Post by arazour on 2012-06-05
fixed it by first removing bumblbee:
```

sudo apt-get purge bumblebee bumblebee-nvidia

```

then removing all fglrx and ati radeon drivers:
```

sudo apt-get purge fglrx fglrx-amdcccle fglrx-dev

```

I found that I've got nvidia drivers too so removed them too:
```

sudo apt-get purge nvidia-current nvidia-common nvidia-settings-updates nvidia-settings

```

then removed /usr/share/ati/ folder:
```

sudo rm -rf /usr/share/ati/

```

then installed ati drivers using this walkthrough:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

now I can log back in to cinnamon ;)

---

