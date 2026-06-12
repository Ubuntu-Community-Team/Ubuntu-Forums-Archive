---
title: "Issue with Display error on startup - 11.10"
date: 2012-03-05
forum: Desktop Environments
---

### Post by powderskier9 on 2012-03-05
Good Day,

First off, thanks for taking the time to look at my issue.

I am running the following Ubuntu version;

Distribution: Ubuntu 11.10 oneiric, 
Desktop Environment: GNOME 2.32.1 (Ubuntu 2011-04-14)
Platform: x86_64

With the following graphics card;

Card: Nvidia GeForce 8800 GTX
Nvidia Driver Version: 173.14.30 

On startup, I am seeing the following error;

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
Could not apply the stored configuration for monitors

none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 327;
CRTC 327 trying mode 3360 x 1050@50Hz with output at 1680 x 1050@50Hz(pass 0)
CRTC 327 trying mode 3360 x 1050@50Hz with output at 1680 x 1050@50Hz(pass 1)
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

If I go into the System Settings->Hardware->Displays->I see an Unknown single monitor listed as 3360 x 1050, clicking on Detect Displays does nothing.

When I go to the NVIDIA X Server Settings configuration->X Server Display Configuration shows;

**Unable to load X Server Display Configuration page: Failed to query NoScanout for screen 0**.

Beneath this setting, I see X Screen 0, showing Dimensions of 3360 x 1050.

Under GPU 0 - (GeForce 8800 GTX), I see both of my monitors listed with the correct settings. 

The monitors both work, they display properly on screen, just seeing the error on startup and the error in the X Server Display Configuration. Hence, I am thinking the issue lies with the xorg.conf file. Prior to having the error shown above in the X Server Display Configuration, both monitors were setup for TwinView.

I have tried to remove the xorg.conf file from /etc/X11, restart then rebuild xorg.conf file, but I still seem to be having this issue.

Any suggestions on the best approach to resolve this issue.

Thanks,

powderskier9

---

### Post by gordintoronto on 2012-03-05
You provided lots of good information, but you missed the most important part: what is the exact brand and model of your monitors? How are they connected to your computer? VGA/DVI/HDMI/Displayport, any adapters to change X into Y?

---

### Post by powderskier9 on 2012-03-06
Sorry about that, here is the remaining info that you had been looking for;

What is the exact brand and model of your monitors? 

LG Flatron W2052TQ, 2 monitors, both the same model.

How are they connected to your computer? VGA/DVI/HDMI/Displayport?

Single DVI cable connection from each monitor connected to DVI ports on the graphics card.

Any adapters to change X into Y?

No adapters to modify connectivity from the monitor to the graphics card.

Please let me know if you need anymore information regarding the above.

Thanks for your help,

powderskier9

---

### Post by gordintoronto on 2012-03-06
Good stuff! I hope someone can provide some help; I don't have a suggestion.

---

### Post by powderskier9 on 2012-03-09
Update to for the error message that I had seen before. 

I went to Application Menu->System Tools->System Settings->Hardware->Additional Drivers->the driver was set to NVIDIA accelerated graphics driver (version 173), shown with green circle indicating this driver was Active ->scrolled down in the list of Additional Drivers and changed the driver setting to Activate the following driver; NVIDIA accelerated graphics driver (post-release updates) (version 173-updates) driver, then restarted the system. The error message that I had seen above went away.

Hopefully this helps someone to resolve an issue such as this one if they happen to encounter it.

Thanks to all for the help.

---

