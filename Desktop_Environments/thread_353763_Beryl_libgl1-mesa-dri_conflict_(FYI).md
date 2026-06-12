---
title: "Beryl libgl1-mesa-dri conflict (FYI)"
date: 2007-02-05
forum: Desktop Environments
---

### Post by Metlin on 2007-02-05
Earlier today, I had some trouble installing Beryl (with Gnome) on Edgy on my Dell e1405 with an Intel chipset. I figured this information might be useful for folks that might do some searching later.

1. The default video driver that Edgy comes with seems to have problem, and for whatever reason, I had nvidia's glx drivers installed. So, I did the following (without X running):

```
sudo apt-get remove --purge nvidia-glx
sudo apt-get remove --purge xserver-xorg-video-i810
sudo apt-get install xserver-xorg-video-i810
```

2. After this, I tried running glxgears and while it ran, it was quite choppy and was being rendered indirectly.

3. This, as it turns out, was because the installation procedure overwrites a version of libgl-mesa that has conflicts with the drivers. So, I installed the latest libgl-mesa driver:

```
sudo apt-get install libgl1-mesa-dri
```

4. After this, I installed beryl and bery-manager and everything seems to work fine.

I did find a couple of other bugs, however:

1. If your screensaver hangs, you can either revert to Xscreensaver or turn it off.

2. Your System -> Quit -> <Hibernate/Sleep/Reboot/Login/Switch User/Shutdown> options disappear, and clicking on the System -> Quit icon seems to reboot.

Turns out that both of these are bugs that have been reported but are yet unresolved. 

Eitherway, I hope someone finds this information useful, and would save them some searching time.

---

### Post by Shootfast on 2007-02-05
The lack of Shutdown buttons is caused by Beryl being started after gnome, however I only had this problem on Dapper. I think if you create a new session for Beryl and run the startup script found on the Wiki [here](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#Configuring_Beryl)  you should be fine.

My problems pertain to the latest drivers on edgy, which don't seem to support the rain effect. Is there a way to revert to the dapper drivers? (which DID work)

---

