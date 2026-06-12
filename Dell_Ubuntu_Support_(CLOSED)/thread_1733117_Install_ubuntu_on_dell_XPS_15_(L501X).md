---
title: "Install ubuntu on dell XPS 15 (L501X)"
date: 2011-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Megaorange1 on 2011-04-18
I just installed Ubuntu on my Dell XPS 15 to dual boot with Win 7. 

1.Some of the buttons like FN+brightnes up/down don't work properly.
2.Is there anyting I can do with my Nividia card?
3.Is there anything important I need to Know about Ubuntu

---

### Post by Megaorange1 on 2011-04-19
Srry for the double post but anyone?

---

### Post by ttshivers on 2011-04-19
As to your buttons not working, it looks like someone found out a solution to this at: [https://bbs.archlinux.org/viewtopic.php?pid=903214]("https://bbs.archlinux.org/viewtopic.php?pid=903214").  Even though its in the Arch Linux forums, it should work for ubuntu.

With our Nvidia card, you can enable desktop effects like a 3d cube and wobbly windows. [http://blog.sudobits.com/2010/10/18/how-to-enable-3d-desktop-effects-in-ubuntu-10-10/]("http://blog.sudobits.com/2010/10/18/how-to-enable-3d-desktop-effects-in-ubuntu-10-10/")

---

### Post by DMGrier on 2011-04-20
make sure you go into your ubuntu software center and install the Nvidia drivers.

---

### Post by ttshivers on 2011-04-20
You might need to enable some drivers from your card under the restricted drivers.

---

### Post by Rio517 on 2011-05-26
How did you get ubuntu installed?  I keep getting "Kernel panic - not Syncing: VFS: Unable to mount root fs on unknown-block" errors.

I've tried to install via usb key and cdrom without luck.

-Rio

---

### Post by maverick280857 on 2011-05-26
> **Megaorange1 said:**
> I just installed Ubuntu on my Dell XPS 15 to dual boot with Win 7. 

1.Some of the buttons like FN+brightnes up/down don't work properly.
2.Is there anyting I can do with my Nividia card?
3.Is there anything important I need to Know about Ubuntu

First off, there's a [thread]("http://ubuntuforums.org/showthread.php?t=1618801") exclusively for this laptop where you might gain the attention of other users more easily.

1. They work fine out of the box for me, but every time I log in, plug in or remove the adapter, the brightness settings get re-set. When you say they don't work properly, what exactly do you mean? Do they work at all?

2. First install the 'additional drivers' from Ubuntu. Go to (Ubuntu Menu)->Administration->Additional Drivers. I assume you have a GT435M?*

3. Stick around on the forums here; you can learn a lot by just playing around while making sure your critical data is always backed up.

PS -- The L501X was customizable, so specifics of the configuration may differ across continents. So it might be a good idea to include specifics of your configuration when posting on this forum.

* - If you need them, you can also get the 'latest' drivers directly from [www.nvidia.com](www.nvidia.com). But they must be installed in console mode (which you can get to, by doing Ctrl+Alt+F1 or in your case Ctrl+Alt+(Fn+F1)), after you stop the gdm service. Most users probably won't require NVIDIA's own drivers, unless they are into programming or something the restricted drivers (from the Additional Drivers section) don't provide.

---

### Post by maverick280857 on 2011-05-26
> **Rio517 said:**
> How did you get ubuntu installed?  I keep getting "Kernel panic - not Syncing: VFS: Unable to mount root fs on unknown-block" errors.

I've tried to install via usb key and cdrom without luck.

-Rio

1. Are you able to boot from the Live CD/DVD?

2. Did you try different USB ports?

3. Do you have the Optimus configuration by any chance? (The Core i7 versions don't, but the L501X also came with Core i5s...)

4. Did you try the 32-bit version or the 64-bit one?

Some other people have reported similar problems. Have a look at these links

[https://bugs.launchpad.net/ubuntu/+bug/774599](https://bugs.launchpad.net/ubuntu/+bug/774599)

[http://fossplanet.com/f10/%5Bbug-774599%5D-%5Bnew%5D-ubuntu-11-04-fails-install-new-dell-xps-15-a-147750/](http://fossplanet.com/f10/%5Bbug-774599%5D-%5Bnew%5D-ubuntu-11-04-fails-install-new-dell-xps-15-a-147750/)

Since you're anyway in the experimental stage, try installing Linux Mint or Fedora 15 (former is closer to Ubuntu 11.04). If you get a similar error, it's got to be due to some hardware problem.

---

