---
title: "Suspend Problem on XPS 410 &amp; Feisty"
date: 2007-06-23
forum: Dell  Ubuntu Support
---

### Post by rozen on 2007-06-23
I have an Ubuntu XPS 410 and a 2707WPF. I am running with the nv drivers and KDE. I have not tried Beryl. Hibernate works fine.  I saw a posting that suspend works out of the box with nv and nvidia drivers.  

My problem is that my machine will go into suspend but will not completely wake up.  That is, the screen does not come alive.  It just remains black.  I am sure that it goes into the suspend state because the power consumption goes from about 80 watts to 2 watts.  When I try to restart it by pushing the power button, the power jumps back up to 80 watts but I can find no way to get the screen to come alive.  I can log in from another machine with ssh and reboot the machine. 

I would certainly appreciate any suggestions to solve my problem.

Thanks in Advance,
Don

---

### Post by karl_kashofer on 2007-06-26
Hi !

I have the same problem, with the nv driver hibernate works, but after suspend to ram the screen does not wake any more. With the nvidia driver its the other way round, suspend to ram works but hibernate dies when hibernating....
[http://ubuntuforums.org/showthread.php?t=480683](http://ubuntuforums.org/showthread.php?t=480683)

This is on a feisty 64 bit system with a XFX Nvidia 7950 and a Asus m2n32 board. Same problem with feist32 and edgy32.

Any pointers very welcome....
Cheers,
Karl

---

### Post by karl_kashofer on 2007-07-01
You might want to try dist-upgrading, for me the new nvidia-glx-new driver Version: 1.0.9755+2.6.20.5-16.29 fixed this.

Cheers,
Karl

---

### Post by rozen on 2007-07-02
I installed the nvidia driver and now suspend is working fine.  Since I am running KDE, I used synaptic to install the restricted-manager package and then installing the nvidia driver was trivial.

Now I would like to be able to awaken my suspended system from the keyboard as well as the power button.  Is there a configuration setting allowing that?    Is there bios support for that?

Thanks,
Don

---

