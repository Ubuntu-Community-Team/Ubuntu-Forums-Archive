---
title: "Gnome/Nautilus style mount from shell?"
date: 2009-12-27
forum: Desktop Environments
---

### Post by Joe_CoT on 2009-12-27
Is the anyway I can replicate the actions taken when I choose to mount a drive from nautilus? I don't mean just a simple mount. When I choose that:
nautilus figures out a mount point based on its label.
makes some sort of temporary mount point?
mounts the drive on that point?

I don't need to use a special method to unmount it; umount works just fine, and the mount point disappears.

Basically, I'm dealing with [LP bug 353387]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/353387"), and while there is a post in there that offers a method for automatically unmounting and remounting, I need something more eloquent than that. I need to a) automatically unmount whatever sd card is mount (which is easy with a combination of mount/grep/unmount), b) automatically mount it again -- which is the part I can't get.

So how does nautilus do it? Is there some plugin that I can't really use? Is there a script I could just run? Is there some subsystem I'm unaware of? I just need to know how it figures out what to call it, and how it creates a temporary mountpoint that goes away as soon as you unmount.[CENTER][/CENTER]

---

### Post by Joe_CoT on 2009-12-27
Nevermind, figured it out. Command is devkit-disks

---

### Post by SecretCode on 2009-12-29
> **Joe_CoT said:**
> devkit-disks

Aha ... that's a useful command ... thanks for the find!

---

### Post by doru001 on 2011-08-14
[devkit-disks has been replaced with udisks]("http://www.linux-archive.org/gentoo-user/331871-devkit-disks-has-been-replaced-udisks.html")

---

