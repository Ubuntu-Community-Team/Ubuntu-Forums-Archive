---
title: "Read ext3 former boot drive"
date: 2010-10-11
forum: Desktop Environments
---

### Post by nolanpro on 2010-10-11
So I upgraded my hard drive and went with a clean Lucid install. But now I want to get files off my old drive. When I re-hooked it back up (now 2 drives in the system), ubuntu refuses to boot.

It kind of boots then just hangs. Never gets to the desktop, and the HD lite on my case is constantly flickering (what could it be doing??)

I have it set up correctly in my BIOS so that the new drive is the boot drive, not the old one.

The only difference is that the new drive is sata and the old drive is old school pata (ide).

I even tried pulling out the old pata drive and hooking it up to a USB adapter I have. Looking at it in the Disk Manager, it shows it as unformatted, and old faithful GParted doesn't even see it!

Now get this: I pulled out my new sata and put back in the old ide drive and guess what, now it wont boot! Grub (probably MBR) is screwed up also!

Any ideas how I can read the data from that old drive? Ether by getting my new lucid install to boot with the old drive as a slave in the system, or by hooking it up externally using USB?

Thanks!

---

### Post by ubunterooster on 2010-10-11
The light usually means a heavy read/write. Listen to the drive while the light is blinking, do you hear a lot of clickings?

It appears the drive has simply died :(

Install gparted and see if that utility can help to see if it can be formatted

---

### Post by nolanpro on 2010-10-11
Thanks, yeah I tried gparted but no luck. I don't think the drive is dead because when its plugged in (by itself) it boots for a bit, then throws me into BusyBox saying something or other is not right. If the drive was dead, I don't think it would even get that far...

---

