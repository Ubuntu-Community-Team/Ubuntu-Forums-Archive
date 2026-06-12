---
title: "NO BLOCK DEVICE: Setting up a USB drive to unlock encrypted system drive at boot."
date: 2009-05-15
forum: General Help
---

### Post by tkarmadragon on 2009-05-15
My main goal is to have a fully-encrypted system drive, that can automatically be unlocked in the presence of a USB drive storing the correct keyfile. This will give me the security of encryption, with the ability to remote shutdown/reboot a headless server without entering a password at boot. 

My main reference is this forum thread here: [http://ubuntuforums.org/showthread.php?t=949870](http://ubuntuforums.org/showthread.php?t=949870)

Everything listed in the HOWTO at the above link seems to be working great..

**EXCEPT**

.. after the system reboots and attempts to read the USB drive, I get a slammed with a NO BLOCK DEVICE error.

I'm using Jaunty 9.0.4 server edition (no gui), fully updated through apt-get, with a 4GB OCZ Rally2 Turbo USB drive. The system drive is encrypted with the default options presented when installing Ubuntu. 

The USB drive mounts perfectly fine once Ubuntu is loaded. I've tried using both ext2 and fat32 partitions, all made using PARTED. I've followed everything in the above HOWTO, understand it step-by-step, and the script executes flawlessly at startup. All relative files, including the keyfile, have root ownership and mod 777 permissions. The USB drive is recognized as device sdb at boot, and the access light on the USB drive flashes while being scanned by the crypt-usb script.

The problem is that after a few seconds the script times-out, spits out a "no block device" error message, then defaults to entering the password manually. I've tried both ext2 and fat32 filesystems, and even added some extra commands to my  /etc/initramfs-tools/modules file:

```

fat
vfat
sd_mod
scsi_mod
sg
usb_storage
```I've exhausted every resource, both in Google and on these forums. I don't know what to do next. The HOWTO linked above is the *only* resource I could find about making bootable USB Keys that stored keyfiles similar to TPM chips. I simply want to have the benefit of an encrypted system drive, while avoiding the game-stopping password prompt that prevents any kind of unattended reboots of a server.

This is the full readout from the initial boot:

```
Boot from (hd0,4) ext2    f66d87ed-cd31-42a4-b8af-1ce903d736b4
Starting up ...
Loading, please wait ...
[    3.080000] crypt-usb: ALIVE
[    3.080000] crypt-usb: Searching for removable keys ... press ESC to cancel
[    7.864686] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.867650] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   18.160000] crypt-usb: no block device found
[   18.160000] crypt-usb: DEFERRED to askpass
Enter passphrase to unlock the disk /dev/disk/by-uuid/3344dc8e-ebb0-4327-8360-3661384a349d (sda1_crypt):
```
I've only been using Ubuntu server for little over a week. I'm a newbie, but a quick learner. I've been able to wrestle past many obstacles using the powers of google and this great forum, but I am completely stumped when it comes to the above error. I have no idea how to fix this problem, please help!  :-)

---

### Post by tkarmadragon on 2009-05-15
I went out and bought a new USB drive today, thinking that (by some slim chance) this was a hardware issue. I purchased a generic 2GB flash drive from Office Depot. I've tried formatting the drive in both ext2 and fat32, with chmod 777 permissions. I'm still having the same problem as described above. :-(

---

### Post by tkarmadragon on 2009-05-16
Well, I finally got this to work!

I tried doing a few things differently from the original guide, such as referencing the usb drive by its unique UUID instead of a label , adding an entry into /etc/fstab, and placing the keyfile in the root of the drive (I think './keys' has trouble being processed by the script).

I'm going to update the original guide with my new changes, and post it in the guide section of the forums. When I do that, I'll post the link here. Looks like I still managed to solve things on my own! :-)

---

