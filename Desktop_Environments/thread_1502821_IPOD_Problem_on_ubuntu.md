---
title: "IPOD Problem on ubuntu"
date: 2010-06-06
forum: Desktop Environments
---

### Post by franket on 2010-06-06
[IMG]http://makeuseof.com/images/wikipedia-on-ipod.jpg[/IMG]

My IPOD is IPod Photo
My OS is Ubuntu
  - Note Book ubuntu hardy - No Problem with IPOD
  - PC ubuntu 9.10 and now 10.04 - have the problem

When i connect ipod to my PC ( on NB no error last 2 line )
dmesg
> 
[ 2258.950066] usb 1-4: new high speed USB device using ehci_hcd and address 3
[ 2259.100077] hub 1-0:1.0: unable to enumerate USB device on port 4
[ 2266.590050] usb 1-4: new high speed USB device using ehci_hcd and address 4
[ 2266.742118] usb 1-4: configuration #1 chosen from 1 choice
[ 2266.784672] Initializing USB Mass Storage driver...
[ 2266.784914] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2266.785603] usbcore: registered new interface driver usb-storage
[ 2266.785611] USB Mass Storage support registered.
[ 2266.793096] usb-storage: device found at 4
[ 2266.793103] usb-storage: waiting for device to settle before scanning
[ 2271.793498] usb-storage: device scan complete
[ 2271.795322] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 2271.796498] sd 8:0:0:0: Attached scsi generic sg4 type 0
[ 2271.803790] sd 8:0:0:0: [sdc] Adjusting the sector count from its reported value: 39063024
[ 2271.803806] sd 8:0:0:0: [sdc] 39063023 512-byte logical blocks: (20.0 GB/18.6 GiB)
[ 2271.807224] sd 8:0:0:0: [sdc] Write Protect is off
[ 2271.807235] sd 8:0:0:0: [sdc] Mode Sense: 64 00 00 08
[ 2271.807241] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2271.809847] sd 8:0:0:0: [sdc] Adjusting the sector count from its reported value: 39063024
[ 2271.812169] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2271.812183]  sdc: sdc1 sdc2
[ 2272.163539] sd 8:0:0:0: [sdc] Adjusting the sector count from its reported value: 39063024
[ 2272.166180] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2272.166195] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 2272.856779] FAT: invalid media value (0x2f)
[ 2272.856789] VFS: Can't find a valid FAT filesystem on dev sdc1.


I can see ipod drive and can transfer file to ipod but slow and when check dmesg again but on NB hardy no problem transfer fast.

> 
[ 2272.856779] FAT: invalid media value (0x2f)
[ 2272.856789] VFS: Can't find a valid FAT filesystem on dev sdc1.
[ 2417.314162] sd 8:0:0:0: [sdc] Unhandled sense code
[ 2417.314172] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2417.314181] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[ 2417.314191] Info fld=0x0
[ 2417.314195] sd 8:0:0:0: [sdc] Add. Sense: No additional sense information
[ 2417.314204] sd 8:0:0:0: [sdc] CDB: Write(10): 2a 00 01 69 1a fb 00 00 f0 00
[ 2417.314223] end_request: I/O error, dev sdc, sector 23665403
[ 2424.161169] sd 8:0:0:0: [sdc] Unhandled sense code
[ 2424.161178] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2424.161186] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[ 2424.161197] Info fld=0x0
[ 2424.161201] sd 8:0:0:0: [sdc] Add. Sense: No additional sense information
[ 2424.161209] sd 8:0:0:0: [sdc] CDB: Write(10): 2a 00 01 69 7d 4b 00 00 f0 00
[ 2424.161228] end_request: I/O error, dev sdc, sector 23690571
[ 2431.612161] sd 8:0:0:0: [sdc] Unhandled sense code
[ 2431.612171] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2431.612179] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[ 2431.612189] Info fld=0x0
[ 2431.612192] sd 8:0:0:0: [sdc] Add. Sense: No additional sense information
[ 2431.612201] sd 8:0:0:0: [sdc] CDB: Write(10): 2a 00 01 69 de bb 00 00 f0 00
[ 2431.612217] end_request: I/O error, dev sdc, sector 23715515
[ 2433.935167] sd 8:0:0:0: [sdc] Unhandled sense code
[ 2433.935177] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2433.935185] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[ 2433.935195] Info fld=0x0
[ 2433.935199] sd 8:0:0:0: [sdc] Add. Sense: No additional sense information
[ 2433.935207] sd 8:0:0:0: [sdc] CDB: Write(10): 2a 00 01 69 fd bb 00 00 f0 00
[ 2433.935223] end_request: I/O error, dev sdc, sector 23723451
[ 2441.744168] sd 8:0:0:0: [sdc] Unhandled sense code
[ 2441.744178] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2441.744187] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[ 2441.744197] Info fld=0x0
[ 2441.744201] sd 8:0:0:0: [sdc] Add. Sense: No additional sense information
[ 2441.744210] sd 8:0:0:0: [sdc] CDB: Write(10): 2a 00 01 6a 67 db 00 00 f0 00
[ 2441.744229] end_request: I/O error, dev sdc, sector 23750619
[ 2446.502158] sd 8:0:0:0: [sdc] Unhandled sense code
[ 2446.502168] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 2446.502176] sd 8:0:0:0: [sdc] Sense Key : Hardware Error [current] 
[ 2446.502187] Info fld=0x0
[ 2446.502190] sd 8:0:0:0: [sdc] Add. Sense: No additional sense information
[ 2446.502200] sd 8:0:0:0: [sdc] CDB: Write(10): 2a 00 01 6a a6 9b 00 00 f0 00
[ 2446.502219] end_request: I/O error, dev sdc, sector 23766683


I try to find solution and I found thread
[https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/456996/comments/8](https://bugs.edge.launchpad.net/ubuntu/+source/gvfs/+bug/456996/comments/8)
I config hal already but it still error

>  lshal -u `hal-find-by-property --key block.device --string /dev/sdc1` 

> 
udi = '/org/freedesktop/Hal/devices/volume_uuid_A88B_3652'
  block.device = '/dev/sdc1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 33  (0x21)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000000FE2D59_0_0'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000000FE2D59_0_0'  (string)
  info.product = 'iPod'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_A88B_3652'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/host8/target8:0:0/8:0:0:0/block/sdc/sdc1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'vfat'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = 'FAT32'  (string)
  volume.ignore = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = 'iPod'  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec', 'utf8', 'shortname=', 'codepage=', 'iocharset=', 'umask=', 'dmask=', 'fmask=', 'uid=', 'flush'} (string list)
  volume.mount_point = ''  (string)
  volume.num_blocks = 80262  (0x13986)  (uint64)
  volume.partition.media_size = 20000267776  (0x4a81bde00)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.size = 41094144  (0x2730c00)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'A88B-3652'  (string)


---

### Post by denstorekalapojser on 2010-06-06
is it jailbreaked? else are it not able to be used by Ubuntu. 

Its a safety  measure Apple have created to be sure you are using iTunes.
My Jailbreaked iPod Touch(3G) works fully with gtkpod from the Ubuntu reposity.

Use Windows or Mac, if you not want to jailbreak it.

---

### Post by franket on 2010-06-06
Thanks denstorekalapojser for reply I'am sorry about topic not clear 

My Ipod is IPOD PHOTO  not IPOD TOUCH or IPHONE I just edit my post for image :)

now I did not upgrade my notebook for 10.04 because this problem.

I get ipod photo from second hand market about 3 - 4 month and I can use with UBUNTU HARDY ( I think 8.04 ) NO PROBLEM. But first I can't use with UBUNTU 9.10 when transfer file to ipod error happen and I can't umount ipod from PC. On UBUNTU 10.04 still error but I can transfer file to ipod ( slow speed about 2 MB/s )

---

