---
title: "Dual Head Support - Ubuntu 7.10"
date: 2008-01-04
forum: Desktop Environments
---

### Post by halberdier25 on 2008-01-04
I'll be quite honest and say that I'm only partially comfortable with using Linux. I mean, I'm perfectly fine using it and stuff, but I'm still not used to it's layout and features and am definitely not used to this xorg.conf stuff.

On my computer, I have an nVidia 8500GT (DVI and VGA/S-video). I dual boot Ubuntu 7.10 and 32-bit Vista. I have dual monitors running perfectly in Vista, but in Ubuntu, it outputs only on the monitor connected to DVI.

I have been looking into the subject, but not with any real zeal as I can live with one monitor. There just doesn't seem to be a whole lot of support on the subject, and having the second monitor sitting there is somewhat annoying if it isn't useful.

I would like to figure out some way to either have one desktop on one screen and one desktop on the other, or one stretched desktop.

1680x1050 - DVI
1280x1024 - VGA

I have read around the forum and can't find a straightforward answer either through my own ignorance or different conditions.

Thanks,

---

### Post by overdrank on 2008-01-05
> **halberdier25 said:**
> I'll be quite honest and say that I'm only partially comfortable with using Linux. I mean, I'm perfectly fine using it and stuff, but I'm still not used to it's layout and features and am definitely not used to this xorg.conf stuff.

On my computer, I have an nVidia 8500GT (DVI and VGA/S-video). I dual boot Ubuntu 7.10 and 32-bit Vista. I have dual monitors running perfectly in Vista, but in Ubuntu, it outputs only on the monitor connected to DVI.

I have been looking into the subject, but not with any real zeal as I can live with one monitor. There just doesn't seem to be a whole lot of support on the subject, and having the second monitor sitting there is somewhat annoying if it isn't useful.

I would like to figure out some way to either have one desktop on one screen and one desktop on the other, or one stretched desktop.

1680x1050 - DVI
1280x1024 - VGA

I have read around the forum and can't find a straightforward answer either through my own ignorance or different conditions.

Thanks,

Hi and welcome, Have you enabled your restricted drivers under system, administration? I you have installed the drivers for you graphics card then you can use nvidia settings to setup your dual monitors. Use the command ```
gksudo nvidia-settings
``` In the terminal located under applications, accessories. Then you can set up using twin view. Good luck and welcome again. :KS
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by halberdier25 on 2008-01-06
Thank you very much.  When I get a chance, I'll try that.

---

### Post by halberdier25 on 2008-01-09
Ok, I don't know your guys' rules on double posting, but I can't figure this out.

I got the control panel up and everything, and got the monitor enabled, but nothing happened.  I applied and rebooted and nothing was there.  I told it to save and I rebooted and now Ubuntu is dead.  It flips between an nVidia shot on the primary screen and code three or four times before it hits a disjointed screen with dialog on the monitor that I can't use because 2/3 is off of my screen and the monitor won't capture it in auto-adjust.  Reformat and reinstall?

---

### Post by smeged on 2008-01-10
I had a similar problem last night, I’ve got a 7300go running dual screens, I enabled the nvidia drivers in the restricted section and ran nvidia-setting, struggled with it for ages as nothing was coming across and then realised that I can save the settings to the xorg.conf. Once I did that restarted X (ctrl + alt + backspace) and then went back into the nvidia-settings then I could configure both monitors, again I saved the settings to the xorg.conf, and restarted X and it worked fine.

Something that might help, my second monitor went a bit silly at one point with the power led flashing on and off and the nvidia-setting couldn’t detect it, I had to unplug the monitor and plug it back in to reset it and after that I had no problems detecting it.

Ps. Backup your xorg.conf file. It will save having to do a complete reinstall. But it sounds like its stuffed up and does need a reinstall in this case 

Hope that helps

---

### Post by halberdier25 on 2008-01-10
Reinstalling AIT.  I had backed it up, but there was no way for me to figure out how to access it because it wouldn't display on the screen correctly, and blindly clicking doesn't always work.

Thanks, though.

EDIT:

I have it, I can get it to work, but because one monitor is 'shorter' than the other, I either don't get the top bar or I don't get the bottom bar.  However, I plan on getting a monitor identical to my current primary which will make the setup simpler.  This whole thing has taught me how to get it to work, for which I am thankful.

---

