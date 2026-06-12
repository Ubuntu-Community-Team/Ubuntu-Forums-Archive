---
title: "Nvidia AntiAlias Override?"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by Drezliok on 2007-04-24
While using Edgy I had Envy to install the newest Nvidia drivers. Which in turn installed a configuration menu for the Nvidia driver. I am using Feisty now and I want to over ride the AntiAlias settings so that WoW looks better. I used to do this all the time.

(If I can)How can I access this menu?


Tnankyou for your time.

---

### Post by cogadh on 2007-04-24
Just do this:
```
sudo nvidia-settings
```
You might not need the sudo, but I think it is required to write changes to the xorg.conf file.

---

### Post by klerfayt on 2007-04-24
> **cogadh said:**
> Just do this:
```
sudo nvidia-settings
```
You might not need the sudo, but I think it is required to write changes to the xorg.conf file.
You should run nvidia-settings as normal user!

---

### Post by Drezliok on 2007-04-24
worked Thankyou

---

### Post by ubnewbie2 on 2007-04-27
> **cogadh said:**
> Just do this:
```
sudo nvidia-settings
```
You might not need the sudo, but I think it is required to write changes to the xorg.conf file.

I tried this, but it gave an error - NV-CONTROL extension not found on this Display, so I installed the restricted driver for nvidia (I have an old TNT Riva installed).  

I tried nvidia-settings again, but this time the error was that the control was too old, 1.6 required (I think).

??

---

### Post by galvheim on 2008-01-12
I struggle a lot about this too. I run Gutsy Gibbon, and apparently I am not able to save the settings I give in Nvidia-Settings. I have tried both with sudo or non-sudo to run this. It saves my settings momentarley to my .nvidia-settings-rc file, but as soon as I reboot it will go back to previous settings. 

Even denying permissin by makeing the file readable only will not keep my file from beeing overwritten later.

I also want to state that I'm running Comiz, and when I run Nvidia-settings from terminal it will tell me that :  

ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       50 of configuration file '/home/gunnar/.nvidia-settings-rc' (no Display
       connection).

---

