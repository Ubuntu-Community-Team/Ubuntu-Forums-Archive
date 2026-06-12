---
title: "No splash, but boots fine..."
date: 2009-02-19
forum: General Help
---

### Post by MysticGold04 on 2009-02-19
I have an Ubuntu 8.04 installation that is working correctly, but cannot see the splash screen when booting. When it is done booting up, the login screen appears normally and works great from there on.  What could be causing the splash screen to not show?  I do see a message on the monitor: 'out of range'  when booting it taking place.  

The machine is a Gateway P4 3.0ghz with an ATI Radeon PCIe video card.

---

### Post by dcstar on 2009-02-19
> **MysticGold04 said:**
> I have an Ubuntu 8.04 installation that is working correctly, but cannot see the splash screen when booting. When it is done booting up, the login screen appears normally and works great from there on.  What could be causing the splash screen to not show?  I do see a message on the monitor: 'out of range'  when booting it taking place.  

The machine is a Gateway P4 3.0ghz with an ATI Radeon PCIe video card.

You can try adding a "vga=" option to your Grub boot string, do a forum search for details.

---

### Post by MysticGold04 on 2009-02-20
> **dcstar said:**
> You can try adding a "vga=" option to your Grub boot string, do a forum search for details.

I tried that and I got the same things mentioned in this post...

```

http://ubuntuforums.org/showthread.php?t=929965&highlight=grub+video+mode
```

Ohwell, its not really that big of a deal since when X starts, the resolution is fine. Thanks for your suggestion though! :)

---

### Post by caljohnsmith on 2009-02-20
Did you recently make any changes to your swap partition? If the UUID of your swap partition changes for any reason, you will lose your Ubuntu splash screen on start up. To see if that might be the issue, how about posting;
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by MysticGold04 on 2009-02-20
Nope, no changes have been made to the swap configuration.  This system is running as installed.  I can even Hibernate it and it comes back just fine.  The problem is that the boot screen resolution seems to be out of range of what the monitor is capable of displaying, because the login screen comes up just fine at 1280x1024.  Also, no shutdown screen displays either when shutting it down... everything else runs normally.

---

### Post by unutbu on 2009-02-20
What happens when you boot with the kernel boot option "vga=normal" ? According to [https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer) this should disable the framebuffer. If you look on that wiki page, they describe a "black screen" problem which sounds like what you are experiencing. The work-around described on that page is to boot with the "vga=normal" option.

---

### Post by alejobar on 2009-02-20
> **MysticGold04 said:**
> I have an Ubuntu 8.04 installation that is working correctly, but cannot see the splash screen when booting. When it is done booting up, the login screen appears normally and works great from there on.  What could be causing the splash screen to not show?  I do see a message on the monitor: 'out of range'  when booting it taking place.  

The machine is a Gateway P4 3.0ghz with an ATI Radeon PCIe video card.

That happened to me long time ago with Ubuntu 8.04 and my Dell Inspiron 6400, to fixi it I downloaded an startup manager from Synaptic, I'm sorry I don't remember the exact name, but look for it in Synaptic, it will allow you to change the splash size, color and type, try different sizes one should work for your pc.

---

### Post by MysticGold04 on 2009-02-20
Thanks, I'll play around with it... like I said, not a huge deal because it works, just a preference.  It does work with the nosplash option.. it shows the text while booting up just fine...

---

