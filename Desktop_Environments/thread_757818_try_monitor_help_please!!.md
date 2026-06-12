---
title: "try monitor help please!!"
date: 2008-04-17
forum: Desktop Environments
---

### Post by versidus on 2008-04-17
**[SIZE="3"]hi guy i just installed ubuntu on my desktop and i cant get my three monitors to work together only one works, i have two Nvidia cards one is a AGP FX 5500 withe one monitor, the other is a PCI FX 5200 with two monitors, im really new at linux so pretty please go slow, im not that smart.....:confused:[/SIZE]**

---

### Post by warp99 on 2008-04-17
Try here:

[https://help.ubuntu.com/community/NvidiaMultiMonitors?highlight=%28monitors%29%7C%28multiple%29](https://help.ubuntu.com/community/NvidiaMultiMonitors?highlight=%28monitors%29%7C%28multiple%29)

---

### Post by versidus on 2008-04-17
**[SIZE="3"]Thank You!! Thank You!! Thank You!!  oh man your a life saver! just one more little question how do i make i one big desktop apposed to three separate desktops?[/SIZE]**

---

### Post by warp99 on 2008-04-17
The program nvidia-settings can set up your configuration to include twinview which allows you to span a single xserver session across several monitors. You can also make an xorg.conf file that can be used to make the changes permanent to your desktop. Here's a guide that will show you how:

[http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup](http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup)

The guide also works with Gutsy 7.10 if you have that version of Ubuntu installed. If you need to make any additional adjustments to you xorg.conf that the nvidia-settings tool does not here is the official nvidia guide to configuring twinview:

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-13.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/chapter-13.html)

and final if you want to run Compiz Fusion graphics with multiple cubes or one big cube install the CCSM manager:

```
sudo apt-get install compizconfig-settings-manager
```

which allows you to override the Ubuntu control panel defaults. Just make sure you have the universe repositories enabled. If you have any more questions please see my signature for helpful tips.

---

### Post by versidus on 2008-04-17
[B][SIZE="3"]thanks for the help, i could not have gotten this far with you.
i got my desk top to be one big desk top, but now the cube and awn don't work.
how do you think i could fix this??? i went to the appearance preferences / visual effects tab and it was on NONE so i clicked on custom and i get a error (Desktop effects could not be enabled) thank you again...[/SIZE][/B]:KS

---

### Post by versidus on 2008-04-18
[B][SIZE="3"]this much i have figured out it was a conflict between compiz Fusion graphics and  xinerama
so i turned off xinerama, and is working fine now, but no one big desktop[/SIZE][/B]:(

---

### Post by versidus on 2008-04-19
**How could I get compiz-fusion to work with xinerama?**

---

