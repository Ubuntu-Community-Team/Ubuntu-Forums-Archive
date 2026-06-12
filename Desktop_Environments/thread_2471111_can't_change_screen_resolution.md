---
title: "can't change screen resolution"
date: 2022-01-21
forum: Desktop Environments
---

### Post by Seadevil on 2022-01-21
only show one screen resolution:  1020x768

my Dell vga monitor is 1920x1080   

how can i fix this?   do i have to reinstall?

i tried    xrandr: Failed to get size of gamma for output default

---

### Post by TheFu on 2022-01-23
What is the GPU and the OS release?

I had an old nvidia GPU that lost support of nvidia proprietary drivers when I moved to 16.04, so only the F/LOSS drivers worked.  It lost 1200p support as a result. No solution was possible, but to wait for the F/LOSS drivers to support that resolution - but by that point, I'd retired the system and built a new box with a new $70 GPU (this was before GPUs were hard to get).

Also, if the system is using Wayland, then X11 commands like xrandr don't work. Is it running Wayland or X11?

3 questions asked. 3 answers needed.
```
$ inxi -bGxxz
```
will provide the answers needed. Please and thank you.  

Of course, we assume the answer isn't here: [https://docs.xubuntu.org/2004/user/C/index.html](https://docs.xubuntu.org/2004/user/C/index.html) and that restricted drivers have been loaded.
```
sudo ubuntu-drivers autoinstall
``` will get the correct drivers for any supported GPU. If any are installed, reboot.

---

