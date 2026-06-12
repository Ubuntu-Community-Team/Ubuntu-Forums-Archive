---
title: "diskless clients with different hardware"
date: 2008-09-25
forum: Desktop Environments
---

### Post by xris_xcess on 2008-09-25
I've decided to setup a diskless environment in the school I work in. Im currently running a Hardy x86 server and Hardy x86 clients.
My pxe booting, netinstall and diskless work, but I've come up against the problem of different hardware on the clients.
I realize that usually when you deploy a computer lab, you tend to setup identical hardware on a number of machines. Unfortunately this is not my case (sort of).

I've got a number of similar machines: Sempron CPU, 1gb ram, Nvidia chipset, nvidia 6100 GeForce video. Now, I setup my system on one of them just as I want to serve it up from the server. Passed it over to the server. Setup the clients to boot into PXE and startup from the server.

First problem. I can't by any means get my nvidia driver/resolution settings to "stick" properly.

When I boot up my setup machine, all is OK. But when I boot a second "similar" machine... the settings are off. Now, I'm not bothered too much about using the restricted drivers (no gaming or heavy graphics here) but I WILL be extremely picky about the resolution.

It seems that the auto configure feature in Hardy does not work too well. I tried "skipping" this by configuring xorg.conf directly, but it doesn't work. Most of my monitors work at 1024x768x60Hz. When I get one machine running properly, I boot up another one... but I'm back at 800x600.

Ideas?

Could I:
1-Create settings for groups of similar/identical machines to be applied as they boot (before gdm and X start).

2-A Script to identify the hardware and write out a xorg.conf for that machine AND that session of X (so as not to interfere with other machines that have already booted).

3-Some how tweak the hardy auto-configure routine for the resolutions that I want (1024x768 in most cases, with some machines at 800x600)... and hopefully load the nvidia driver for those machines that can use it.

4-Give up, it's too hard with a mixed setup.

by the way, I followed the guide at [https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto).

I guess, instead of doing a nfsroot, I could build a squashfs image for groups of machines and just share the /home over nfs , and save some space.

Anyone with some experience with this kind of setup?

---

