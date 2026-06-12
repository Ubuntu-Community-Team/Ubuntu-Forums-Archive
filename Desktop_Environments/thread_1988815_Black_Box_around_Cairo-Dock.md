---
title: "Black Box around Cairo-Dock"
date: 2012-05-28
forum: Desktop Environments
---

### Post by Dark Ninja on 2012-05-28
Hello,
I'm new to this forum and fairly new to GNU/Linux as a primary distro, however I have used it off and on on VM's and random boxes laying around the house. So, for the most part, I know how to do everything I want but now I'm stumped! Right now I'm running Ubuntu 11.10 with Fluxbox as the WM. I like it because of how lightweight it is and Gnome is too **** bulky! So, with Fluxbox I installed Cairo-Dock and added it in my .fluxbox/startup file and all is well except I get the black box around it blocking off a fairly good chunk of real estate on my monitor. I know this is an issue of compositing and although I could of used compiz and see multiple "solutions" for that, I opted for Cairo Composite Manager. Had a few issues finally getting it installed (which we won't get into) but finally did and added that to my .fluxbox/startup file as well. Now when I log in my Dock starts but the black box is still around it. However, all the other visual effects are working fine. Everything else has transparency, even the sub-menus of Cairo, but not the main dock itself! Any help guys??
I ran the following thinking it might be a driver issue (which seemed unlikely since all other visuals worked):
 ```
sudo lshw -C display
```and this is my output:
```
  *-display               
       description: VGA compatible controller
       product: G84 [GeForce 8600 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:19 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:bc00(size=128) memory:fe7e0000-fe7fffff

```So...looks like my nvidia driver is installed and working correctly, no? This is where I start to get fuzzy so I could be looking at this all wrong so ANY help is apreciated!
THANKS IN ADVANCE!!

---

### Post by zombifier25 on 2012-05-28
I haven't used Cairo Dock for a while, but only in WMs that supports compositing like Compiz does Cairo Dock displays properly. In other VMs, the transparency are actually fake transparency.

---

### Post by JOHNNYG713 on 2012-05-28
you have to enable composting, same as docky ! google is your friend ! how to enable composting in ubuntu

---

### Post by Dark Ninja on 2012-05-28
> **ZOMBIFIER25 said:**
> I haven't used Cairo Dock for a while, but  only in WMs that supports  compositing like Compiz does Cairo Dock  displays properly. In other VMs,  the transparency are actually fake  transparency.
:mad: I was afraid of that...I'm not giving up quite yet though! Thanks!

> **JOHNNYG713 said:**
> you have to enable composting, same as docky ! google is your friend ! how to enable composting in ubuntu
Thank you, and yes, Google is my friend!  :P I'm sorry for not clarifying, I do have "Composite Desktop" checked and I've tried both the "X-Rendering" and "Software Rendering" settings for cairo-compmgr to no avail.

---

