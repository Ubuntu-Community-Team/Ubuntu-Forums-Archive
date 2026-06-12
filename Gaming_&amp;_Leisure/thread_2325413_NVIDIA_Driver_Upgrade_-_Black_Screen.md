---
title: "NVIDIA Driver Upgrade - Black Screen"
date: 2016-05-22
forum: Gaming &amp; Leisure
---

### Post by EdwardEnglish on 2016-05-22
Hey guys, I hope you can help me

I have a GeForce 950 and downloaded the latest driver just yesterday. I made it so I can run it as a programm, killed the x-server and went to terminal by strg+alt+1 to start the installation. It went fine to the point where it said it encountered an error, not being able to use "nvidia-drm" when building DKMS - abort! I was not able to get back to my desktop, because the x-server said it could not find any screens. I found online that I could *purge *all nvidia related stuff and so I did - and after one reboot I was able to get back to my desktop. 
When I checked the driver it even said, that I was using the current nvidia driver I actually failed to install. I just had to reinstall nvidia-settings and even the settings programm said, I was using the current driver (the one i downloaded from nvidia homepage).

When I tried to start steam, it said i was missing > libGL.so.1 and so I found this page [http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005) and executed both commands

```
sudo apt-get install --reinstall libgl1-mesa-glx:i386
```

and

```
sudo apt-get install --reinstall libgl1-mesa-dri:i386
```

I have to add that the first time I entered the first command it said that I have unmet dependencies, but after trying the second command the first one went through, too. 
I did a reboot and found a black screen. Nothing seems to work anymore. Can you help me?

---

### Post by EdwardEnglish on 2016-05-22
Hey guys i was able to solve it myself:

- press SHIFT when booting to get to grub and to terminal
- delete the x-server config file and reinstall xserver and  xserver-core
- re-run the nvidia.run file (I still had it saved in my home folder) and select NOT to build DKMS
- the nvidia-setup will install all 32Bit Libraries and build a new xserver config file

after reboot everything was back to normal

---

### Post by MikeCyber on 2016-05-22
The first time I install nvidia with synaptic, as it installs headers etc. Later updates from Nvidia site work fine after that.

---

