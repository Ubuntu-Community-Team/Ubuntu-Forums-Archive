---
title: "apt upgrade - Preventing GRUB"
date: 2020-09-24
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-09-24
Satellite Laptop 1GB Hard Drive

Folks,

I have a triple boot system, Ubuntu 18:04, Fedora KDE and Winoz10

I also run an external drive of 320GB partitioned to experiment with other distros.  Grub menu appears if I alter BIOS to boot directly to external drive.

On my main system I have disabled os_prober and I boot my three internal systems and my external drive using my own entries in /etc/grub.d/40_custom

All fine and happy with it **except **for some reason if I boot in to my external drive and an update involves **update-grub** for some reason it trashes my grub menu on my main drive and I end up in the grub prompt (Not grub rescue).

Now this is not an issue, I can set root, set location of vmlinuz and initrd.img and the root directory, boot in to Ubuntu 18:04.  I then reinstall GRUB, run update-grub and all is back to normal.

I've checked partition mount points but as yet cannot fathom why updating my external disk trashes the menu on my internal drive but I can deal with that, what I'd like to know, if anyone can offer a suggestion, is how can I prevent an update-grub running if I do an apt update then upgrade.

Geoff

---

### Post by oldfred on 2020-09-24
Ubuntu's Ubiquity only installs grub to first drive or your internal drive.
I always add an ESP to may external drives & larger flash drives with full installs.
And I force Ubiquity to install to the ESP on the external drive.
External devices with UEFI only boot from /EFI/Boot/bootx64.efi. 
An internal entry is created with 'ubuntu' but that may overwrite your internal installs UEFI entry and make external drive required to boot.

Check your fstab entry for mount of ESP. I expect it is the UUID of your internal drive.
cat /etc/fstab
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

If old BIOS install, grub keeps a file with reinstall drive.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive. 

I used to have to totally reinstall grub or restore my /EFI/ubuntu folder. But found only differnce is /EFI/ubuntu/grub.cfg, a three line file that uses grub's configfile to find full grub.cfg in the install. I now just edit that if install goes into wrong ESP.

I have done test installs pf Debian & Fedora (more just to see how grub is handled) and they let me choose my sdb drive and installed grub' UEFI boot files to ESP on sdb.

---

### Post by Geoff_Lane on 2020-09-24
Thank you for very quick reply.

Being a laptop the internal HD is not easily accessible.  There is no HD compartment, all base screws need removing plus a spudger to remove case.  Easy enough, done it to upgrade memory but time consuming.

The BIOS is pathetic, very limited options even the advanced options give me very little to alter.

I'll delve in to the mount points again but they seem OK to me.  What puzzles me is if I leave the external drive plugged in up comes a GRUB menu with all my Operating Systems showing but if I unplug the external drive the GRUB menu doesn't appear and I end up at the grub prompt.  This suggests something needed to boot ends up on external drive so something gets altered on the internal drive.

Also, to add to the confusion if I plug the external drive in at boot time then lsblk shows the external drive as the first drive.

I'll pore through your comments above but at least with your advice some months back I am able to recover a lost menu and adjust my manual entries.

Geoff

---

### Post by oldfred on 2020-09-24
Then you are booting from the external drive.
Part of grub is in the internal drive, but rest is on external.
So without external drive you only get grub> as it cannot find the external drive.

---

### Post by Geoff_Lane on 2020-09-24
So bearing in mind without external drive connected it usually boots fine so then something must be over writing or deleting entries on the internal drive.

If at grub boot you press 'E' for edit my main system is similar to;
> set root='hd0,gpt5'
linux /boot/vmlinuz-4.15.0-115-generic root=/dev/sda5
initrd /boot/initrd.img-4.15.0-115-generic
boot

There are a few other lines but the above is sufficient to boot in to my system; I am guessing this is nothing to do with UEFI booting.

Geoff

---

### Post by oldfred on 2020-09-24
That is just a manual boot.
You are in effect creating your own boot entry that would normally be in grub menu.

If you have full grub in (hd0,5), you may be able to do this:
configfile (hd0,5)/boot/grub/grub.cfg

That is similar to what is in /EFI/ubuntu/grub.cfg

```
fred@z97-focal-kubuntu:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid db535ec5-b653-4627-9f21-2645e1d7ca4e root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


```

---

### Post by Geoff_Lane on 2020-09-29
> **oldfred said:**
> That is just a manual boot.
You are in effect creating your own boot entry that would normally be in grub menu.

If you have full grub in (hd0,5), you may be able to do this:
configfile (hd0,5)/boot/grub/grub.cfg

That is similar to what is in /EFI/ubuntu/grub.cfg

```
fred@z97-focal-kubuntu:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid db535ec5-b653-4627-9f21-2645e1d7ca4e root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


```

I have exactly that (Different disk IDs naturally) but not the first line you show being [B]cat /boot/efi/EFI/ubuntu/grub.cfg

[/B]Geoff

---

### Post by oldfred on 2020-09-29
The cat command is just to list it.

But if your configfile in your ESP does not boot but manual boot does, something must not match.
Check UUID & hdX gptY , that they match the partition your install is in.

It may then just need a reinstall of grub, not just the update-grub which refreshes menu.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you can boot, you can reinstall grub from inside your install also.
sudo dpkg-reconfigure grub-efi-amd64-signed
sudo grub-install --bootloader-id ubuntu /dev/sda  
#if drive with esp is sda and correct ESP mount is in fstab.

---

### Post by Geoff_Lane on 2020-09-30
Thank you,  I'll recheck my UUIDs against the device paths etc.

I never had a problem with Grub-legacy, easily able to install to disk or/and partitions, different image backdrops, menu lists fine.  

Grub2 capable of more but complex.

Geoff

---

