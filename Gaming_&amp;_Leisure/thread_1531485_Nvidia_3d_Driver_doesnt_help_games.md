---
title: "Nvidia 3d Driver doesnt help games"
date: 2010-07-15
forum: Gaming &amp; Leisure
---

### Post by Gene393 on 2010-07-15
Hi, I wondered why games like teeworlds and secret mayro chronicles would run painfully slow (really, really slow) and found that ubuntu wouldnt install a nvidia driver cos its not open source software, so I gave it permission and it installed, but now games like secret mayro chronicles wont even start, they go to the startup loading screen then quit, whats up with that?

---

### Post by Gene393 on 2010-07-15
bump

---

### Post by cascade9 on 2010-07-15
Bumping before 24hrs has passed is considered rude.....

How did you install the nVidia drivers?

---

### Post by Gene393 on 2010-07-15
> **cascade9 said:**
> Bumping before 24hrs has passed is considered rude.....

How did you install the nVidia drivers?

sorry, didnt know that, up the top right corner there should be a green video card icon, it will say something abut restricted drivers and you just press activate, then a short download will take place

---

### Post by Perfect Storm on 2010-07-15
Please post Output of:

```
lspci |grep VGA
dmesg |grep NVIDIA
glxinfo | grep direct
cat /etc/X11/xorg.conf

```

Also if you have an onboard card and a videocard in same machine it's advisable to disable the onboard card in the BIOS. It can make conflicts.

---

### Post by Gene393 on 2010-07-15
shaun@Deep-Thought:~$ lspci |grep VGA
02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce G210] (rev a2)
shaun@Deep-Thought:~$ dmesg |grep NVIDIA
[   12.793433] nvidia: module license 'NVIDIA' taints kernel.
[   13.046922] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
shaun@Deep-Thought:~$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
shaun@Deep-Thought:~$ cat /etc/X11/xorg.conflspci |grep VGA
cat: /etc/X11/xorg.conflspci: No such file or directory
shaun@Deep-Thought:~$ dmesg |grep NVIDIA
[   12.793433] nvidia: module license 'NVIDIA' taints kernel.
[   13.046922] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
shaun@Deep-Thought:~$ glxinfo | grep direct
direct rendering: Yes
    GL_EXT_depth_bounds_test, GL_EXT_direct_state_access, 
shaun@Deep-Thought:~$ cat /etc/X11/xorg.conf

---

### Post by Perfect Storm on 2010-07-15
Seems the driver is installed correctly and working. (Note that nvidia GT200 is a very low end onboard card)
Next would be to run smc from the terminal.

---

### Post by Gene393 on 2010-07-17
Dont, worry, I upgraded to Lucid Lynx and it fixed the problem, thanks

---

