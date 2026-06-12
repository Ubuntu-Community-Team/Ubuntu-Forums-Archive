---
title: "FAT32, USB HD and root user problems"
date: 2006-08-12
forum: Desktop Environments
---

### Post by o_O on 2006-08-12
Well, as the title says, I have an external hard drive, using a USB connection, with two partitions formatted using FAT32. 
For some time, it worked just fine, it mounted and I had r/w acces to everything in there. But lately it's been preventeing the computer from actually booting (it would take ages to detect this drive at boot-up (before GRUB loads), if at all). As a result, I had to unplug it so GRUB would load and I could use my computer, and plug it back once Ubuntu was running.

The problem, as you may have already guessed, is that now the partitions aren't even mounted. Somehow, root seems to be the owner, when it shouldn't. Mounting manually (even as root with "sudo su") gives me a "special device /dev/sdb1 doesn't exist" error, and the same for /dev/sdb2, which are the disk's partitions.

This is what fstab looks like for me:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sda6       /media/Files vfat    iocharset=utf8,umask=000  0    0
/dev/sdb1       /media/Backup   vfat    defaults,uid=1000,gid=1000,umask=077,utf8 0 0
/dev/sdb2       /media/Storage  vfat    defaults,uid=1000,gid=1000,umask=077,utf8 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0     0

Where /media/Backup and /media/Storage are the partitions I cannot use anymore. /media/Files is in an internal SATA drive and works just fine.

And this is mtab:

> /dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
/dev/sda6 /media/Files vfat rw,iocharset=utf8,umask=000 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

dmesg gives errors related to the USB drive like so:

> [17182625.588000] usb 2-1.4: device not accepting address 120, error -71
[17182630.476000] usb 2-1.4: new high speed USB device using ehci_hcd and address 121
[17182630.696000] scsi157 : SCSI emulation for USB Mass Storage devices
[17182630.696000] usb-storage: device found at 121
[17182630.696000] usb-storage: waiting for device to settle before scanning
[17182642.268000] usb 2-1.4: reset high speed USB device using ehci_hcd and address 121
[17182642.340000] usb 2-1.4: device descriptor read/64, error -71
[17182642.516000] usb 2-1.4: device descriptor read/64, error -71
[17182642.692000] usb 2-1.4: reset high speed USB device using ehci_hcd and address 121
[17182642.764000] usb 2-1.4: device descriptor read/64, error -71
[17182642.940000] usb 2-1.4: device descriptor read/64, error -71
[17182643.116000] usb 2-1.4: reset high speed USB device using ehci_hcd and address 121
[17182643.524000] usb 2-1.4: device not accepting address 121, error -71
[17182643.596000] usb 2-1.4: reset high speed USB device using ehci_hcd and address 121
[17182644.004000] usb 2-1.4: device not accepting address 121, error -71
[17182644.004000]  157:0:0:0: scsi: Device offlined - not ready after error recovery
[17182644.004000] usb 2-1.4: USB disconnect, address 121
[17182644.004000] usb-storage: device scan complete

And a whole lot of messages like the above, with different adresses, always error -71.

So the question is: Is there a way to recover ownership of the drive (without formatting if possible) or to use it at least (as my user if possible, having to use it as root would be a royal pain in the ***)?

---

### Post by o_O on 2006-08-13
Mounting manually as root didn't work either. It seems the device is not detected. 

Any ideas?

---

