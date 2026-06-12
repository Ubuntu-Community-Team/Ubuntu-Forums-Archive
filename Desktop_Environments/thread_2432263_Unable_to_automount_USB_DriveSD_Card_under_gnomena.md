---
title: "Unable to automount USB Drive/SD Card under gnome/nautilus"
date: 2019-11-29
forum: Desktop Environments
---

### Post by phaenze on 2019-11-29
I am no longer able to automount USB drives and SD Cards under gnome/nautilus. I have tried what I could and have tracked it down (using journalctl -f) to the following gio error code: "Unable to mount volume <volume name>: Gio.IOErrorEnum: Not authorized to perform operation" (please see below for complete error message). It seems that others are also experiencing the same issue, with one user commenting that it started after an update on 13 Nov 2019 - [https://askubuntu.com/questions/1190098/allow-user-to-mount-usb](https://askubuntu.com/questions/1190098/allow-user-to-mount-usb). I order to track this down, I have done the following:
1. I can mount it from gnome-disks when run with sudo and properly access my files.
2. I can mount it as root and properly access my files.
3. I can mount it with pmount w/o root and properly access my files.
4. I have used dconf and checked that both org.gnome.desktop.media-handling.automount & org.gnome.desktop.media-handling.automount are both set to true.
5. I created a new regular user. The USB drive automounts without difficulty. "journalctl -f" reposrts the following: dbus-daemon[8658]: [session uid=1001 pid=8658] Successfully activated service 'org.gnome.Shell.HotplugSniffer'.
6. I then reset gnome completely (dconf reset -f /org/gnome/).

But, still, no joy.

I have been unable to find much on the gio error, and using "gio mount -l -i" shows me info about the drive, but shows nothing as to why I can't access it (complete message below).

Any help would be greatly appreciated.

Paul 




*******Complete error message************
kernel: usb 1-1: new high-speed USB device number 10 using xhci_hcd
kernel: usb 1-1: New USB device found, idVendor=05e3, idProduct=0727
kernel: usb 1-1: New USB device strings: Mfr=3, Product=4, SerialNumber=2
kernel: usb 1-1: Product: USB Storage
kernel: usb 1-1: Manufacturer: Generic
kernel: usb 1-1: SerialNumber: 000000000250
kernel: usb-storage 1-1:1.0: USB Mass Storage device detected
kernel: scsi host1: usb-storage 1-1:1.0
mtp-probe[6307]: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1"
mtp-probe[6307]: bus: 1, device: 10 was not an MTP device
upowerd[1709]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0
upowerd[1709]: unhandled action 'bind' on /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1
kernel: scsi 1:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0250 PQ: 0 ANSI: 0
kernel: sd 1:0:0:0: Attached scsi generic sg1 type 0
kernel: sd 1:0:0:0: [sdb] 30535680 512-byte logical blocks: (15.6 GB/14.6 GiB)
kernel: sd 1:0:0:0: [sdb] Write Protect is off
kernel: sd 1:0:0:0: [sdb] Mode Sense: 0b 00 00 08
kernel: sd 1:0:0:0: [sdb] No Caching mode page found
kernel: sd 1:0:0:0: [sdb] Assuming drive cache: write through
kernel:  sdb: sdb1
kernel: sd 1:0:0:0: [sdb] Attached SCSI removable disk
gnome-shell[2936]: Unable to mount volume 16 GB Volume: Gio.IOErrorEnum: Not authorized to perform operation



*******gio -l -i output************
Drive(2): Generic STORAGE DEVICE
  Type: GProxyDrive (GProxyVolumeMonitorUDisks2)
  ids:
   unix-device: '/dev/sdb'
  themed icons:  [drive-removable-media-flash-sd]  [drive-removable-media-flash]  [drive-removable-media]  [drive-removable]  [drive]
  symbolic themed icons:  [drive-removable-media-symbolic]  [drive-removable-symbolic]  [drive-symbolic]  [drive-removable-media]  [drive-removable]  [drive]
  is_removable=1
  is_media_removable=1
  has_media=1
  is_media_check_automatic=1
  can_poll_for_media=0
  can_eject=1
  can_start=0
  can_stop=0
  start_stop_type=shutdown
  sort_key=01hotplug/1575048722403748
  Volume(0): 16 GB Volume
    Type: GProxyVolume (GProxyVolumeMonitorUDisks2)
    ids:
     class: 'device'
     unix-device: '/dev/sdb1'
     uuid: 'FDA3-5A9B'
    uuid=FDA3-5A9B
    themed icons:  [media-flash-sd]  [media-flash]  [media]
    symbolic themed icons:  [media-flash-symbolic]  [media-symbolic]  [media-flash]  [media]
    can_mount=1
    can_eject=1
    should_automount=1
    sort_key=gvfs.time_detected_usec.1575048722671682

---

### Post by phaenze on 2019-12-02
This ended up being a strange rights issue. I removed my user account from two groups - vboxusers and chrome-remote-desktop - and now can automount without a problem. I haven't been able to reproduce this issue with a test account as regular user or as administrator.

---

### Post by andyliang on 2020-10-12
Thank you soooooo much!!! It finally works after I removed my account from chrome-remote-desktop and rebooted!!!!!!

---

