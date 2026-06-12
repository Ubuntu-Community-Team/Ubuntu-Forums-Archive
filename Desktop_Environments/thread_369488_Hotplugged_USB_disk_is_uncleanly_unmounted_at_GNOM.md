---
title: "Hotplugged USB disk is uncleanly unmounted at GNOME logout"
date: 2007-02-24
forum: Desktop Environments
---

### Post by Jonie on 2007-02-24
Suppose you hotplug USB flash disk, copy or delete something and then just shut down computer without using eject option first. When GNOME quits, it just destroys pmount link, leaving cached data in unknown state. I've done that twice, once with flash disk, the other time with USB hard drive. In both cases the FAT/ FAT32 filesystem became corrupt. There was no hardware malfunction nor kernel instability. Of course, when you use eject option or wait long enough for the buffers to be flushed, everything's ok. It may happen that after corruption kernel will silently mount filesystem ro, leaving user wondering "why can't I copy files to my mp3 anymore".

I experienced this on Edgy, but other versions may also be affected.

Is there a workaround?

---

### Post by yabbadabbadont on 2007-02-25
> **Jonie said:**
> Is there a workaround?
There sure is:
> **Jonie said:**
> Of course, when you use eject option ...

:D

---

### Post by Jonie on 2007-02-27
Sure, got a cup of Ubuntu and that makes one smile right away, doesn't it? :)

Speaking seriously, however, can't GNOME just unmount such user mounted disk, in case you have too many icons on the desktop so you may forget?

Something's wrong anyway. Why should I eject something I don't necessarily want to eject?

---

### Post by yabbadabbadont on 2007-02-28
> **Jonie said:**
> Sure, got a cup of Ubuntu and that makes one smile right away, doesn't it? :)

Speaking seriously, however, can't GNOME just unmount such user mounted disk, in case you have too many icons on the desktop so you may forget?

Something's wrong anyway. Why should I eject something I don't necessarily want to eject?

I'm not disagreeing with you.  Not to start a "Holy War" or anything, but Gnome is known for it's lack of options when it comes to stuff like this.  If you were to ask a Gnome dev this question, he would probably stare at you blankly for a moment, and then ask you why you would ever want to unmount it without ejecting it...  :lol:

I would also suggest that you could setup a script to run at logoff that would check and unmount volumes if needed, but I have yet to find anyone who knows how to get Gnome to run anything at logoff time.

Personally, I don't use automount for anything.  I just run Fluxbox and use Gkrellm to manually mount and unmount volumes as needed.  (via the built-in filesystem plugin)

---

### Post by Jonie on 2007-02-28
I can imagine that eventual solution outside GNOME might rise more problems than there yet exist. First, you may have pmounted disks from other session, that should not be unmounted. You cannot harness init to do this either as the disks are not in fstab.

To sum the things up, why am I getting so angry at this. If you wanted to customize bootable flash, each "ejection" means that usb controller will not recognize disk at next boot. If so, you would have to wait for GRUB, press a key to prevent linux from loading further, then replug pendrive, then "ctrl+alt+del", then boot menu, cause BIOS will forget about absent boot device... If you've done so, say, 20 times in a row then you would know :)

---

