---
title: "Ubuntu won't boot anymore"
date: 2008-12-17
forum: General Help
---

### Post by DManX04 on 2008-12-17
I select it at the boot loader, it goes to the splash screen like normal, and then I get this:

```
Gave up waiting for root device. Common Problems:
-Boot args (cat/proc/cmdline)
   -check rootdelay = (did the system wait long enough?)
   -check root = (did the system wait for the right device?)
- missing modules (cat/proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/E2A407FDA407D2C9 does not exist. Dropping to shell!
```

It then goes to the shell and just say to type help for a list of commands. All that's on the screen is this:

```
(initramnfs)_
```

Not really sure what to do about this.

---

### Post by taurus on 2008-12-17
Does your machine boot into recovery mode from GRUB menu?

If not, can you boot your machine with the LiveCD?  You need to have a look at /boot/grub/menu.lst (on harddrive) to make sure the UUID matches your root partition, /.

Open a terminal from the LiveCD and post the output of this command here.

```
sudo fdisk -l
```

---

### Post by Irony on 2008-12-17
When it gets to the grub menu use your cursor to move up and down to the partition you want to boot to (it may already be on it) and press e (for edit).

Where it says /dev/???? replace your iuud number with the actual device for example hda2 or sda2 or whatever it is.

Then I think you hit enter - it tells you what to do at the bottom of the screen.

After you've booted up you can manually edit your menu.lst file so you don't have to keep editing it on boot up.

---

