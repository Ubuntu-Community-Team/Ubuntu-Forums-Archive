---
title: "NVIDIA drivers not installing properly?"
date: 2010-01-07
forum: Desktop Environments
---

### Post by woodyson on 2010-01-07
This is my first post on the forum.  I am new to Ubuntu, but have some Unix experience (shells only, not X-windows) from work.

I have successfully installed Ubuntu Server 9.04 (Jaunty) in what is currently a dual boot with Vista and then added ubuntu-desktop (the plan is triple boot so I need grub legacy, so I am following [http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)).  Works fine in low graphics mode, but Vista manages 1024 by 768 on this old Dell 15" monitor.  

I have found some useful info in other posts about adding the NVIDIA drivers and I have tried this but I don't think they install correctly and I have ended up re-booting into recovery mode and using xfix (just re-booting gives Failed to load the NVIDIA kernel module - Screens found but none have a usable configuration).  The reason I don't think the NVIDIA installation was OK is that the installation window only briefly appears (the first time was longer when files were downloaded) and just disappears without any message.  Does the installation write to a log somewhere so I can see what is happening?

For info:
sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 7100/nForce 630i
       vendor: nVidia Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0

Vista shows me:
Adapter Type: NVIDIA GeForce 7100/NVIDIA nForce 630i 
PCI bus 0, device 16, function 0 
Valid Modes include: 1024 by 768, True Color (32 n=bit), 60 Hertz 
Monitor Type: Generic PnP Monitor

Thanks in advance for any suggestions.

---

### Post by woodyson on 2010-01-08
I have found the log I needed: /var/log/dkms_autoinstaller which contained:

nvidia (180.44): Installing module.
  Kernel headers for 2.6.28-17-server are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.28-17-server or equivalent.

Installing this package and re-booting worked and I can now used 1024x768 resolution.

---

