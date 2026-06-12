---
title: "fluxbox mouse"
date: 2016-12-06
forum: Desktop Environments
---

### Post by kc_2 on 2016-12-06
I installed fluxbox, when I startx it, I see the mouse cursor at the top left of the screen but it doesn't move when I move the mouse, although if I right-click on the mouse, the menu pops up, and I can move the "invisible" cursor through the menu, highlighting menu items. How do I lock the cursor back in with the mouse?

---

### Post by kc_2 on 2016-12-07
Maybe it's an xorg thing.

---

### Post by kc_2 on 2016-12-08
{sorry, bumping this... googled it but haven't found anything yet.}

---

### Post by kc_2 on 2016-12-08
Bump.

---

### Post by kc_2 on 2016-12-09
[COLOR=#000000][INDENT]Bump.[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by sudodus on 2016-12-09
I have tested fluxbox a few times, and I had no problem with the mouse/cursor. I have made systems from Ubuntu mini.iso and Ubuntu Server with fluxbox.

What operating system is it, where you installed fluxbox? Did you start from Ubuntu mini? Or some other linux distro?

And which version is it? Have you checked that the mouse works with another desktop environment in the same computer?

Or did you install fluxbox alongside a standard desktop environment, for example Unity?

---

### Post by kc_2 on 2016-12-09
> **sudodus said:**
> I have tested fluxbox a few times, and I had no problem with the mouse/cursor. I have made systems from Ubuntu mini.iso and Ubuntu Server with fluxbox.

What operating system is it, where you installed fluxbox? Did you start from Ubuntu mini? Or some other linux distro?

And which version is it? Have you checked that the mouse works with another desktop environment in the same computer?

Or did you install fluxbox alongside a standard desktop environment, for example Unity?

Thank you for your reply.

It's Ubuntu Server. I started with the base install of that system.

It's the most recent version (16.10).

The mouse works great in another system on the same computer.

I did not install any desktop environments.

So far, all I've done:

[LIST]
[*]installed ubuntu server (with no add-ons during the setup)
[*]installed fluxbox xorg nmon nmap htop hwinfo lftp
[/LIST]

---

### Post by sudodus on 2016-12-10
I think I have installed **xinit** (and xterm) to my 'mini' systems with a GUI.

-o-

If you have a 64-bit processor, you can try to install a mini system from a compressed image file (developed from the Ubuntu Server 16.04 LTS 64-bit iso file) described at the following link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

The mouse works in the computers, where I have tested it. If that system works, it is likely that the mouse should work for you too, if you start from an Ubuntu Server 16.04 LTS iso file (I think both 32-bit and 64-bit).

If you have a 32-bit processor, please tell me, and I can suggest other 'mini' alternatives to try.

---

### Post by kc_2 on 2016-12-10
> **sudodus said:**
> I think I have installed **xinit** (and xterm) to my 'mini' systems with a GUI.

-o-

If you have a 64-bit processor, you can try to install a mini system from a compressed image file (developed from the Ubuntu Server 16.04 LTS 64-bit iso file) described at the following link,

[Installation/UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

The mouse works in the computers, where I have tested it. If that system works, it is likely that the mouse should work for you too, if you start from an Ubuntu Server 16.04 LTS iso file (I think both 32-bit and 64-bit).

If you have a 32-bit processor, please tell me, and I can suggest other 'mini' alternatives to try.

I could reinstall the entire system, I haven't done much with it yet other than set up the LVM with the RAID drives, although am hoping to resolve the mouse issue without a full system reinstall. :( Maybe it's something in the configuration, an xorg setting. I don't know.

---

### Post by sudodus on 2016-12-10
It could also be a problem with a driver or firmware. What graphics card/chip is it (brand name and model)? Have you tried some versions (16.04.**1** LTS and 16.10) of Lubuntu live, booted from DVD or USB, 'Try Lubuntu without installing'? Do that before re-installing.

---

### Post by kc_2 on 2016-12-11
> **sudodus said:**
> It could also be a problem with a driver or firmware. What graphics card/chip is it (brand name and model)? Have you tried some versions (16.04.**1** LTS and 16.10) of Lubuntu live, booted from DVD or USB, 'Try Lubuntu without installing'? Do that before re-installing.

That might be it. I'm using a separate video card. I can try connecting the monitor's cable up to the motherboard. D'oh! I completely forgot about that. :) It could very likely be a driver/firmware issue. It's a Gigabyte GeForce GTX 1070 8GB Windforce OC Video Card. There's a page somewhere, it might even be on ubuntu's site, about how to use cards like that one (it's nvidia) in linux. I suppose it is possible to physically unplug and plug the cable back in every time I reboot between systems, but am hoping to not have to do that. The video card works fine in CLI, but yeah maybe it needs the firmware to make it work in GUI in linux.

That's a good idea about live versions of linux. I'll give that a try.

I found the link to that page:
[https://wiki.debian.org/VGAPassthrough](https://wiki.debian.org/VGAPassthrough)

I haven't tried that out yet but who knows maybe it'll work.

Another edit: it looks like that page is not going to help, it's for using VM-based applications and this is the base OS running on the machine.

---

### Post by kc_2 on 2016-12-13
[COLOR=#3E3E3E][COLOR=#272A34][FONT=&quot]I reinstalled xorg xserver-xorg fluxbox, and then ran dpkg-reconfigure xorg. Installed nvidia firmware. On reboot, it ended up automatically loading the GUI and I don't want that. Actually, I don't even want the GUI installed, it's an entire desktop environment, or at least the login page to one, not just a window manager. My guess is that xserver-xorg or the nvidia addition installed it and dpkg-reconfigure set it up to auto-load the GUI. I want to remove anything I don't need. (Don't need a desktop environment, just fluxbox). Trying this out on a VM but the mouse works fine there, so it's not exactly the same as the main system that's having the mouse problems. Not sure what would need to be done in xorg.conf type files if it's that.[/FONT][/COLOR]
[/COLOR]

---

### Post by sudodus on 2016-12-14
You wrote in one post, that you use the version 16.10. It is a short-life version, only 9 months (from the release in October).

There are several advantages with the version 16.04.1 LTS. It is supported for 5 years, until April 2021, and it is debugged and polished. It is likely to work well with most hardware, maybe with the exception of very new hardware.

So I suggest that you try to do the 'same exercise' with 16.04.1 LTS. Maybe the mouse will work in fluxbox.

---

### Post by kc_2 on 2016-12-15
> **sudodus said:**
> You wrote in one post, that you use the version 16.10. It is a short-life version, only 9 months (from the release in October).

There are several advantages with the version 16.04.1 LTS. It is supported for 5 years, until April 2021, and it is debugged and polished. It is likely to work well with most hardware, maybe with the exception of very new hardware.

So I suggest that you try to do the 'same exercise' with 16.04.1 LTS. Maybe the mouse will work in fluxbox.

I considered going with LTS but thought the most recent would be fine. That could very well be the reason for the mouse issue. The mouse works fine with 16.10 and fluxbox when I run the system as a VM, but that's also using the mouse driver from the host OS. I might give 16.04.1 a try.

---

