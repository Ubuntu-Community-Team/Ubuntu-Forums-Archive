---
title: "Loss of Usplash After Resizing Partition"
date: 2009-04-10
forum: General Help
---

### Post by Pidgin on 2009-04-10
I have Ubuntu 8.10 installed on one partition of the type ext3. I resized an NTFS partition and the Ubuntu partition, getting some space from the NTFS partition and gave it to the Ubuntu partition. The operation was done by gparted using the Ubuntu 8.10 Live CD on a USB flash disk. After the operation, no data loss was found and both Ubuntu and Windows could boot normally. The only problem is that usplash only shows partially.
You see, usplash has two stages. In the first stage, a block just moves left and right and left and right, and you won't know the progress. While in the second stage, the progress will be shown. In my case, the first stage shows, but the second stage is replaced by the text-mode boot, which shows much information on the boot process.
In /boot/grub/menu.lst, the options passed to the kernal are the default: "quiet splash"
I don't know how to solve that. Any clue is appreciated. Thank you!

---

### Post by Pidgin on 2009-04-10
Has not anyone tried to resize the Ubuntu partition?

---

### Post by drs305 on 2009-04-10
It may be a UUID change that is causing this behavior. Run this command to see if the swap UUID is still registered properly:
```
sudo blkid -c /dev/null | grep 'swap'  && cat /etc/initramfs-tools/conf.d/resume
```

If they are different, edit this file and change the RESUME UUID to the same as the result from the "blkid" command. Once you have made the change, run the second command to update the system: 
```

gksu gedit /etc/initramfs-tools/conf.d/resume
sudo update-initramfs -u

```
Reboot when desired.

---

### Post by warpasylum on 2009-04-10
Hmmm... That's really strange. I've redone partitions before and my GRUB broke completely. Don't know if this would help, but have you tried reinstalling your GRUB? Super GRUB Disc does it really easily.

---

### Post by Pidgin on 2009-04-11
> **drs305 said:**
> It may be a UUID change that is causing this behavior. Run this command to see if the swap UUID is still registered properly:
```
sudo blkid -c /dev/null | grep 'swap'  && cat /etc/initramfs-tools/conf.d/resume
```

If they are different, edit this file and change the RESUME UUID to the same as the result from the "blkid" command. Once you have made the change, run the second command to update the system: 
```

gksu gedit /etc/initramfs-tools/conf.d/resume
sudo update-initramfs -u

```
Reboot when desired.

It works! Thank you!
The UUIDs mismatch. After editing /etc/initramfs-tools/conf.d/resume, the problem is solved.
Will the mismatch cause other problems?

---

### Post by drs305 on 2009-04-11
> **Pidgin said:**
> It works! Thank you!
The UUIDs mismatch. After editing /etc/initramfs-tools/conf.d/resume, the problem is solved.
Will the mismatch cause other problems?

The mismatch may have also have disabled your swap. You can check your fstab setting to see if the swap is listed by UUID and make sure it matches the *blkid* UUID. Here are the commands to run to check. You can see if swap is working by running the first command. If it produces all zeros your swap is probably not working. If it is just the middle number (used) that is zero that is ok.
```

free -m  # check swap usage
sudo blkid -c /dev/null | grep 'swap'  # Get swap UUID
cat /etc/fstab | grep 'swap'  # Get fstab swap listing
sudo cp /etc/fstab /etc/fstab.backup   # Back up fstab if need to edit it
gksudo gedit /etc/fstab  # Open fstab to change the UUID of swap
sudo swapoff -a && sudo swapon -a    # Restore swap with new fstab settings
free -m   # Check swap

```

---

### Post by Pidgin on 2009-04-12
> **drs305 said:**
> The mismatch may have also have disabled your swap. You can check your fstab setting to see if the swap is listed by UUID and make sure it matches the *blkid* UUID. Here are the commands to run to check. You can see if swap is working by running the first command. If it produces all zeros your swap is probably not working. If it is just the middle number (used) that is zero that is ok.
```

free -m  # check swap usage
sudo blkid -c /dev/null | grep 'swap'  # Get swap UUID
cat /etc/fstab | grep 'swap'  # Get fstab swap listing
sudo cp /etc/fstab /etc/fstab.backup   # Back up fstab if need to edit it
gksudo gedit /etc/fstab  # Open fstab to change the UUID of swap
sudo swapoff -a && sudo swapon -a    # Restore swap with new fstab settings
free -m   # Check swap

```

As you said, swap was off. But after typing "free -m", I found that only the middle number was zero. I confirmed that swap had been off from gparted, which showed that the swap partition had not been mounted.
After I edited /etc/fstab and restarted the machine, swap went well.

---

