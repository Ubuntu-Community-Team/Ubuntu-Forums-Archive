---
title: "Steam 64 bit install/14.04"
date: 2015-08-20
forum: Gaming &amp; Leisure
---

### Post by w0rstn4m33v3r on 2015-08-20
Having some issues installing steam, so far I managed to get steam-launcher to install but when I try to run it from Dash nothing happens and I no longer get any errors.

At first I was having issues where I didn't have the 32 bit libraries on 14.04, not sure if I solved that issue or during a uninstall/reinstall or something else messed up.

/e I tried the solutions [here]("http://ubuntuforums.org/showthread.php?t=2242632") and it seemed to install the 32 bit libraries, but steam still doesn't open or give errrors after reinstalling

this is my latest error

w0rstn4m333r@Bob:~$ steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1439401440)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

---

### Post by R33D3M33R on 2015-08-20
The error message indicates that either your driver isn't installed properly or you don't have 32-bit libraries for the driver installed. What is your GPU and what driver you are using (run glxinfo from mesa-utils to find out)?

---

### Post by w0rstn4m33v3r on 2015-08-20
I managed to get it to run with
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-349 nvidia-settings
sudo add-apt-repository -r ppa:xorg-edgers/ppa
```

---

