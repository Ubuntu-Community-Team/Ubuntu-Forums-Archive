---
title: "NVIDIA settings not applying at startup"
date: 2009-11-09
forum: Desktop Environments
---

### Post by bigeslp on 2009-11-09
I have set my brightness/contrast to settings other than the default via the NVIDIA settings app/interface. The settings take effect immediatly and I save the file. However, everytime that I log out and back in, the settings are never applied until I start the NVIDIA settings interface. I have found that by using the command nvidia-settings -l in the start-up apps that this will apply the settings. When I use that command it sets the defautl values. I still have to start NVIDIA and close it to apply my settings. 

I have looked at the nvidia-setting-rc file and notice that all of the values that I have changes are set to 0. 

Any idea how I can auto-apply my settings at start-up withoiut have to first start NVIDIA and close it. I suppose I could manually edit the nvidia-settings-rc file and place my brightness and contrast values there, but I dont want to have to edit this file everytime that I make an adjustment via the NVIDIA app. Thanks, Erich

---

### Post by wojox on 2009-11-09
Open a terminal:

```
gksudo nvidia-settings
```

Set your brightness/contrast as root and it will stick.

---

### Post by bigeslp on 2009-11-09
I tried gksudo nividia-settings from the terminal and once it starts the adjusted brightness / contrast settings are applied. I make sure that I save the file and then exit the NIVIDA interface. It still defaults back to original settings with nvidia-settings -l and the nvidia-settings-rc file remains unchanged.

---

### Post by bigeslp on 2009-11-09
Well I have been trying everything that I can think of on this. I have sort of made this work but my solution does not seem right....

If i run gksudo nvidia-settings and change the color and save the files it will not update the .nvidia-settings-rc file.

If I run nvidia-settings (without gksudo) I can change the brightness, contrast ans such, save the file and the nvidia-settings-rc updates and such. Then the nvidia-settings -l command on startup will apply the correct values.

However, running it in user mode if I try to change the resolution it will not let me as I can not create the xorg.conf backup file. 

I am wondering if something on my end is messed up, or if this might be a bug. Its rather tedious to have to run nvidia-settings both with gksudo (to change resolution, but not brightness) and without (to change brightness ect...). 

Also any settings made while in gksudo mode for the brightness do not save in the nvidia-settings-rc file, however, if I exit the nvidia interface and restart it, the settings made while in the previous gksudo seesion are active/remembered. Could there be 2 different config files, each way of running it using a different one?

Erich

---

### Post by Joe Ker1086 on 2009-11-09
> **wojox said:**
> Open a terminal:

```
gksudo nvidia-settings
```

Set your brightness/contrast as root and it will stick.

Does the same concept apply with audio settings? audio always starts full blast (kinda a problem when im at work)

---

### Post by 3Miro on 2009-11-09
IIRC nvidia-setting manager doesn't save any settings, i.e. the thing must be running in order to set/see anything.

Once running, however, you should be able to change resolution and such, I know I can do it.

If you have permission errors, check the permissions on the corresponding folders and files.

---

### Post by tula on 2009-11-10
i have the same problem with you bigeslp, I just realise that this is not my problem lonely, I'm using acer aspire 4530 with gforce 9100mg chipset

---

