---
title: "hide mounted hard drives on desktop"
date: 2008-03-20
forum: Desktop Environments
---

### Post by kei-clone on 2008-03-20
I'm running gutsy dual booting with two other windows partitions that are automatically mounted when I start up ubuntu. I want to keep them mounted, but I don't want them showing icons on the desktop. In addition, I'd like to have other removable media, such as USBs and CDs, keep showing icons when they're mounted. Is there a way I can hide the hard drive icons only?

---

### Post by Bruce M. on 2008-03-20
> **kei-clone said:**
> I'm running gutsy dual booting with two other windows partitions that are automatically mounted when I start up ubuntu. I want to keep them mounted, but I don't want them showing icons on the desktop. In addition, I'd like to have other removable media, such as USBs and CDs, keep showing icons when they're mounted. Is there a way I can hide the hard drive icons only?

Press alt+f2 or use the terminal

```
gconf-editor
```

From there browse

> applications > nautilus > desktop

and you'll have those options.

Yes you'll still see USBs an CD there as you use them.
Bruce

---

### Post by kei-clone on 2008-03-20
hmm, I just tried it with a USB drive mounted. doing this removed the USB icon from the desktop :(

---

### Post by MickS on 2008-03-20
How do you do the same thing with Kubuntu?
Thanks.

Mick

---

### Post by Bruce M. on 2008-03-20
> **kei-clone said:**
> hmm, I just tried it with a USB drive mounted. doing this removed the USB icon from the desktop :(

Really!  When I was using Gnome it worked great. and also when I plugged in a USB device, nautilus opened it as well.  :(

More research I'm afraid.

> **MickS said:**
> How do you do the same thing with Kubuntu?
Thanks.

Mick

I have no idea, try a new making a new thread: KDE: Hide Mounted Drives

See what that does.

---

