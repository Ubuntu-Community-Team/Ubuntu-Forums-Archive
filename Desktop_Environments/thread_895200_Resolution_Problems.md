---
title: "Resolution Problems"
date: 2008-08-19
forum: Desktop Environments
---

### Post by Looshin on 2008-08-19
I recently installed new nvidia drivers and ran into a bit of a problem, I no longer have the option to increase my resolution beyond 640x480. I ran xorg.conf and attempted to add 1680x1050 as an extra mode but this did nothing. 

I've looked through a couple threads on the matter however everyone seemed to have slightly different problems from myself and none of the other solutions worked, first I attempted to change nvidia to read "nv" however then when I tried to run the nvidia settings manager it told me the drivers weren't running, one interesting thing I feel I should note that this did seem to have one positive effect, when I went into  the screen resolution menu it suddenly recognized my monitor which is something it doesn't do when the nvidia drivers are running properly.

Any suggestions would be greatly welcome.

---

### Post by nickgaydos on 2008-08-19
Did you try reinstalling your video driver with EnvyNG instead of the normal Restricted Drivers? I wish I could help you by posting mine, but I have ATI :(

---

### Post by Looshin on 2008-08-19
Sorry I have no idea what EnvyNG is, I simply installed them by running the command outside of the X Server, they seem to work as I now have compositing which is something that refused to work beforehand it's only the resolution which is giving me problems.

---

### Post by nickgaydos on 2008-08-19
> **Looshin said:**
> Sorry I have no idea what EnvyNG is.
EnvyNG is a program that lets you install drivers . I have found it better than the ubuntu restricted drivers.
> Sudo Apt-get install envyng-gtk

---

### Post by Looshin on 2008-08-20
I'll be sure to try that if I don't find any alternatives, I'd like to avoid reinstalling the drivers since the compositing is working which means the drivers are too.

---

### Post by Looshin on 2008-08-23
EnvyNG didn't work, it claims there aren't any versions of the drivers compatible with my video card (a Nvidia 9600GT) and refuses to install, any other suggestions? It really doesn't strike me as a reason to reinstall the drivers anyways as the one currently installed is working.

---

### Post by Looshin on 2008-08-27
Anyone?

---

### Post by Ms_Angel_D on 2008-08-27
Try the following

First go to System » Administration » Hardware Drivers and make sure the Nvidia Accelerated Graphics Driver enabled

the run:
```
sudo apt-get install nvidia-settings
```

then press alt+f2 and run:

```
sudo nvidia-settings
```

Go to "X Server Display Configuration", select your resolution of choice, click on "Apply", and then click on "Save to X Configuration File". 

You may need to reboot to see the changes


I had my resolution mysteriously change on me the other day and had to reset my xorg.conf through nvidia-settings, so maybe it will help.

---

### Post by Looshin on 2008-08-27
Thanks for the suggestion, the Nvidia drivers did not show up in the Hardware Drivers list, however unfortunately following the installation you suggested I was unable to select a resolution greater than 640x480 from the Nvidia menu. At any rate I think I'm going to call a quits, I think I'll be going back to Slackware.

---

