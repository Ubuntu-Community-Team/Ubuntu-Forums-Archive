---
title: "Nvidia drivers"
date: 2008-06-01
forum: Desktop Environments
---

### Post by SlightlyRemoved on 2008-06-01
Hi. I've been having some problems with my graphics card and the nvidia settings. 
Still a bit new to linux so I was hoping someone here can help me

I'm running ubuntu 8.04 - AMD64 and my card is a 8800GT.
I install the nvidia software and restart the xserver and everything works fine. 
It starts up with a very low resolution (640x480) but I just edit my xorg.conf to fix that.

The problem is that when I restart my pc, it has renamed my xorg.conf file and replaced 
it with the original one (from before the installation) and if I try running the nvidia config, it says it can't do it and I have to install the software all over again.

Any help would be great
Thanx

---

### Post by jaakan on 2008-06-01
Do you have nvidia-glx-new installed or nvidia-glx or did you use envy?

---

### Post by Tomatz on 2008-06-01
Completely remove the drivers via synaptic (completely remove) then restart your box and reinstall them.

If you cant start x after the reboot and are presented with the cli type:

```
sudo apt-get install nvidia-glx-new
```

then

```
sudo shutdown -r now
```

---

### Post by Xiong Chiamiov on 2008-06-01
[Try this out.]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329")

---

### Post by SlightlyRemoved on 2008-06-02
Problem fixed. :)
Thanks a lot for the help

---

