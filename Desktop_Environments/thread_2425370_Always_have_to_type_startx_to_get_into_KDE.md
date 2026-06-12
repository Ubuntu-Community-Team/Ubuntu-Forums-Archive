---
title: "Always have to type startx to get into KDE"
date: 2019-08-24
forum: Desktop Environments
---

### Post by rpra006 on 2019-08-24
Hi,
I had a issue with xserver and i followed following instructions to fix it and this did fix the issue but now i have to type **startx** to get into kde everytime i reboot or restart the laptop.
I followed following instructions to fix my original xserver issue and after these steps i have to always type startx
remove:
     ```
sudo apt-get remove --purge xserver-xorg
```
install:
     ```
sudo apt-get install xserver-xorg
```
reconfigure:
     ```
 sudo dpkg-reconfigure xserver-xorg
```

Following command does not seem to to anything for me  sudo dpkg-reconfigure xserver-xorg , is it suppose to prompt for any inputs from the user? 

thanks for all your help.

---

### Post by CatKiller on 2019-08-25
In purging everything related to the X server you likely also took out the Display Manager, which starts X and puts up the login window. I think it's SDDM for Kubuntu.

```
sudo apt install sddm
``` or ```
sudo dpkg-reconfigure sddm
``` should do it, depending on whether you uninstalled it in your first step or simply deselected it.

---

### Post by rpra006 on 2019-08-25
Thanks for that, that solved it.

---

### Post by Artim on 2019-08-25
Please[COLOR=#0000ff]** mark it solved!**[/COLOR]  So others can benefit.

---

