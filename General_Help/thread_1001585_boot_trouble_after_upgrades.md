---
title: "boot trouble after upgrades"
date: 2008-12-04
forum: General Help
---

### Post by gwark on 2008-12-04
I installed Ubuntu 8.04 on a personally assembled destktop a couple of months ago.  It's been working fine until today.  I rebooted after accepting upgrades (including to the kernel) a couple of days ago, I've not been able to reboot since.  

I have spent a fair bit of time looking through forums and found other similar problems, but nothing that is apparently just the same.

When booting in recovery mode (kernel 2.6.24-22-generic) I get the following:

```

[   29.314367] ACPI: PCI interrupt for device 0000:00:1f.5 disabled 
Done.
       Check root= bootarg cat /proc/cmdline
       or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/1e* does not exist.  Dropping to a shell!

```

With other kernels listed in the grub menu, the error is the same.

Following the suggestions in other threads (particularly [here](http://ubuntuforums.org/showpost.php?p=5080524&postcount=6)), I booted from the LiveCD and: 

Used fdisk -l to confirm that things should be booting from /dev/sda1 (my linux partition). 
Used blkid to find the UUID for /dev/sda1 and confirm it is the same as that given in the error prior to dropping to shell.  
Checked menu.lst and /etc/fstab, where everything was in agreement as far as the UUID for /dev/sda1 was concerned.  

It seemed that when other people had the problem I'm having, it was fixed by adjusting the UUIDs in menu.lst and fstab to be in agreement.  

Any help would be appreciated.

Thanks

---

### Post by caljohnsmith on 2008-12-04
How about trying this: reboot, and when you get the Grub menu on start up, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end add the following:
```
rootdelay=120
```
Press enter to save the change, and then "b" to boot. That has worked for a number of users who have gotten the exact same type of error as you. If that doesn't work, also add along with the rootdelay option:
```
acpi=off
```
And see if that does the trick. Let me know how it goes.

---

### Post by gwark on 2008-12-04
I tried adding each of those and have the same message on dropping into the shell.  The only difference is that after adding the second one, the last thing to show up before the error is:

```

[     0.000000] hub 8-0:1.0: 6 ports detected
Done.

```

---

### Post by gwark on 2008-12-06
Is there a way to undo the upgrades after booting up with the liveCD?  Or perhaps something else to try to see if I can get things working again?

---

### Post by gwark on 2008-12-06
Still having trouble after trying some other ideas I found while searching through the forums, but I'm hoping that perhaps what I've found may help narrow the search.

I changed all the UUID references to /dev/sda1 in fstab and menu.lst.  After doing this, the boot process proceeded and hung up at the same spot as before.  However, this time it read:

```

[   29.314367] ACPI: PCI interrupt for device 0000:00:1f.5 disabled 
Done.
       Check root= bootarg cat /proc/cmdline
       or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/sda1 does not exist.  Dropping to a shell!

```

---

