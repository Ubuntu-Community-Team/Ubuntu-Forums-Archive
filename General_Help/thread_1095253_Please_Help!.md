---
title: "Please Help!"
date: 2009-03-13
forum: General Help
---

### Post by bobby1991 on 2009-03-13
Hello,
I recently installed Ubuntu 8.10 via Wubi on my computer that was originally using Windows Xp.
I had no problem logging in to either OS and it was working fine however about an hour ago i attempted to boot windows and it began to scan my usb memory stick for errors, it then became stuck and i was forced to hard reboot and now neither Windows Xp or Ubuntu will boot.
Ubuntu does not load fully and displays the following message:

[B]Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sda1 sda1 -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sda5 /root ntfs-3g force 0 0
Could not mount the partition /dev/disk/by-uuid/44cc5ad2cc5abe3c. This could also happen if the file-system is not clean because of an operating system crash, or an interrupted boot process, or beacause of an inproper shutdown, or if a removable device was unplugged without unmounting/ejecting it first. To fix this, simply reboot into Windows, let it fully start, log in,ideally run a chkdsk /r, then gracefully shut down. Once you restart, you should be able to resume the installation. (filesystem = ntfs, error code = 15)

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) bult in shell (ash)
Enter 'help' for a list of built in commands.[/B]

If i select Windows it will begin to load then a blue error screen flashes and the computer automatically reboots to the boot menu.

Im very new to linux and my skill with Windows XP is very limited so could you please help me
Thanks,
Robbie

---

### Post by pytheas22 on 2009-03-13
It looks like your Windows file system became corrupted, probably as a result of the hard shutdown, and since wubi installs Ubuntu within the Windows file system, Ubuntu also can't boot.

To fix the problem, you will need to fix the Windows file system, which I think you can do using the chkdsk command in the Windows terminal (but I'm no expert on Windows troubleshooting, so you should research how to use chkdsk).  If you continually press F8 while Windows is booting, it might be able to boot into recovery mode instead of going to the blue screen.  Once in recovery mode, you could use chkdsk to fix the file system.

If recovery mode won't work or won't boot, I think your only other option is to boot to the Windows installation CD, which should have an option for repairing a corrupted system.  Hopefully this will work.

In a worst case, you can boot to an Ubuntu live CD and use it to back up your files to external media (you may need to force-mount the Windows partition by typing 'mount -t ntfs-3g /dev/sda1 sda1 -o force' in Ubuntu), then wipe the drive clean and reinstall Windows/Ubuntu.

---

