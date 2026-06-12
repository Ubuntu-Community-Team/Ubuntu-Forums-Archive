---
title: "Can't logout of lxde with 14.04.2 LTS after installing cuda 7.0"
date: 2015-07-24
forum: Desktop Environments
---

### Post by c_xy on 2015-07-24
Hello,

I'm running ubuntu 14.04.2 LTS server with the lxde. Everything has been working fine. I could logout, reboot, shutdown, etc.

We have a dell poweredge r730 server.

I recently installed CUDA 7.0 to take advantage of our Tesla K10 GPU. After installation, I cannot logout of an lxde session. 


EDIT: When I try to shutdown or reboot I get the following error message:

GDBUS.Errorrg.freedesktop.DBus.Error.AccessDenied: Operation not permitted

I can't reboot when clicking the icon on the bottom panel on the left side or right side.  The server will reboot if I type:

> sudo reboot


If I type

> lxsession-logout

The options panel window appears, I click logout, and then I just get the lxde default desktop screen.

The only time I was able to logout successfully is when I first typed:

> sudo lxsession-logout

only a blue screen with the terminal window appeared without the borders

Then I typed within the borderless terminal window

> lxsession-logout

And that logged me out to  lxde login screen.

I can switch user, hibernate, and suspend. But I cannot logout of a lxde session. When I attempt to logout, the panels disappear, and only the lxde default desktop screen and mouse cursor remains. But I can't do anything without  restarting from the poweredge machine. 

This problem happened after the CUDA 7.0 installation.

Any help would greatly be appreciated.

Here is some info:

```
 sudo lshw -C display
  *-display               
       description: 3D controller
       product: GK104GL [Tesla K10]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:33f0-33ef iomemory:33f0-33ef irq:32 memory:92000000-92ffffff memory:33fe0000000-33fefffffff memory:33ff0000000-33ff1ffffff
  *-display
       description: 3D controller
       product: GK104GL [Tesla K10]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: iomemory:33f0-33ef iomemory:33f0-33ef irq:32 memory:91000000-91ffffff memory:33fc0000000-33fcfffffff memory:33fd0000000-33fd1ffffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: G200eR2
       vendor: Matrox Electronics Systems Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0 maxlatency=32 mingnt=16
       resources: memory:90000000-90ffffff memory:93800000-93803fff memory:93000000-937fffff


```

Thanks.

c

---

### Post by c_xy on 2015-07-26
The logout problem was solved by doing a fresh reinstall of 14.04.2 LTS. Then manually installing the correct nvidia drivers, and then installing cuda 7.0 using the run file instead of the package installation. Doing those 3 steps in that order allowed me to continue logout of from the server computer.

There is still an issue with rebooting and shutting down from the panel as opposed to the command line or the computer button. But at least for now, I can logout.

c

---

