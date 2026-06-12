---
title: "nvidia-glx-new problem"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by kreira on 2008-01-16
hi there, My problem is that I can't enable the desktop effects. I did the following: As I am a new Ubuntu user I lost it :P. Firstly I downloaded the nvidia-settings thing. Then, I updated the ubuntu, and after that I went to System -> administration ->Restricted Drivers Manager
and tried multiple times to enable the Nvidia  graphics driver and I get the following message

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb: trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia-settingsE: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb: trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia-settings

As I am a noob user of Ubuntu I tried to erase the file nvidia-settings but it tells me that I dont have the authentication to do it.

What should I do? (except from going back to vista)

---

### Post by FuturePilot on 2008-01-16
In a terminal (Applications>Accessories>Terminal)
```
sudo apt-get remove --purge nvidia-settings
```
The Nvidia Settings panel is also included in the driver. I'm not sure why that separate package is still in the repos.
Then you can try the Restricted Driver Manager again
Once you install the driver and reboot you can launch the Nvidia Settings by pressing Alt+F2 and typing 
```
nvidia-settings
```

---

### Post by lacroixmouz on 2008-01-16
It worked fine. But my resolution was screwed up when I restarted it. How can I enable the cool feature with the cube desktop?( oh my god I am such a nab:P)

---

### Post by FuturePilot on 2008-01-16
> **lacroixmouz said:**
> It worked fine. But my resolution was screwed up when I restarted it. How can I enable the cool feature with the cube desktop?( oh my god I am such a nab:P)

You can change the resolution by
```
gksudo nvidia-settings
```
Then change the resolution and save to X configuration file.
Then for the desktop effects go System>Settings>Appearance and click the Visual Effects Tab.

---

