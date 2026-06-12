---
title: "Software updater failed on reboot, kernel panic"
date: 2023-02-11
forum: Desktop Environments
---

### Post by Major Newb on 2023-02-11
I ran software updater last night, and it indicated that it completed normally and asked me to reboot. I assume that is was updating the kernel from 5.15.0-58-generic to 5.15.0-60-generic. On reboot, I received a bunch of messages ending with "kernel panic: No working init found." Using the advanced boot options, I found that .58 version was available. It indicated major disk problems and said to run fsck, which I did. I pressed "y" about a hundred times, and then .58 booted normally while .60 still produces a kernel panic. I then saved all my personal files. Right now, .58 seems to be running normally, and Software Updater runs with no problems.

I want to avoid reloading the OS, as I have custom WiFi and printer software that requires extra effort, as well as Virtual Box. And yes, the have been running happily through many updates. What are my options?

---

### Post by grahammechanical on 2023-02-12
Be careful. Software Updater removes excess Linux kernels leaving the latest two. Another kernel update will remove the .58 kernel. And you will have the latest kernel which we hope will work and the .60 kernel which we know is broken. Update using the terminal for a while.

```
sudo apt update
sudo apt upgrade
```

Something you might want to try is to install Synaptic Package Manager and search for 5.15.0-60-generic. Synaptic should give you an option to re-install the broken kernel. That might work. Afterwards run

```
 sudo update-grub
```

Watch the printout.

Regards

---

### Post by thumper76 on 2023-02-27
I'm having the exact same problem. You posted two weeks ago. I'm surprised the people responsible for kernel updates aren't more interested in this problem. This is a major issue!!

---

