---
title: "Mounting a phone with a SD card in 8.10"
date: 2008-12-22
forum: General Help
---

### Post by adlin5000 on 2008-12-22
I have a LG VX8350 phone (Qualcomm based) with a 1gig micro SD in it. With 8.4 and earlier all I had to do to access the card was connect it with the usb cable and set the phone to usb mode. Ubuntu would do the rest. After I upgraded to 8.10 when I plug in the phone, Ubuntu detects it as a mobile modem and when I set it to usb mode I get a "usb drive" that wont mount. I get a "Unable to mount location" "Can't mount file" error. I have looked around the forums and it seems like a lot of people have been having issues with phones, but I cant find any solutions.


I hope that someone can figure this out, because I finally got everything working they way I like it on 8.10 and I'd hate to have to reinstall 8.4 and start over.

---

### Post by JacksonJimbo on 2008-12-22
Did you try it with sudo mount.

Can you post your fstab file pls.

Regards 

Jackson

---

### Post by adlin5000 on 2008-12-22
Not sure how to mount it by hand. How would I do that?

Here's the fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=44a24d2b-1a65-4f2c-94d1-5ea22aecc6c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=d2ed9f8f-14b0-4422-8e3b-1ee53ad03a3e /media/sda1     ext3    relatime        0       2
# /dev/sdb1
UUID=fc5b0faf-45a6-45fc-82c6-e2dd4e8ce4a2 /media/sdb1     ext3    relatime        0       2
# /dev/sdb2
UUID=ec37fd79-6e66-425c-89a4-6098ab0c066d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by jay li on 2008-12-22
Error like these "Unable to mount location" "Can't mount file" etc, basically occurs because two things: 

1. You unplug the usb/sd while Windows was on hibernation state.
2. You unplug the usb/sd from Windows without performing "Remove hardware in safe mode". 

So there is a chance it's corrupted and sometimes format might help to fix it.

As for the "Hibernation" cause, just plug your usb/sd back to your machine and perform "Remove hardware in safe mode".

---

### Post by sedawk on 2008-12-22
Before pluging in your phone clear the message buffer ("sudo dmesg -c")
then connect the phone and switch it to usb mode.
Then post the output of "dmesg" here.

The output of dmesg should tell you the device assigned to the
phone. So next step is to show the output of "fdisk -l /dev/sdX"
where "X" is the letter (a-z) you find in the dmesg output.

If the file system is fat32 you might be able to use "fsck" to repair
it. If it is NTFS you have to boot XP/Vista to repair it (if my knowledge
is still up-to-date, I migrated lots of data from NTFS to ext3 because
repairing NTFS was such a cumbersome task).

(Please ignore Jay Li's tip of using "format". Don't do that!
 I think he meant fsck.)

---

### Post by adlin5000 on 2008-12-22
Here is the dmesg output. I'll try doing a windows remove hardware and see if that does anything.

EDIT: Did a remove hardware on my roommates windows computer. no change. Also I tried it with a USB/microSD adapter and got the same results.


```
dmesg
[ 3365.392029] usb 1-9: new full speed USB device using ohci_hcd and address 6
[ 3365.604691] usb 1-9: configuration #1 chosen from 1 choice
[ 3365.607467] cdc_acm 1-9:1.0: ttyACM0: USB ACM device
[ 3371.428293] usb 1-9: USB disconnect, address 6
[ 3372.884021] usb 1-9: new full speed USB device using ohci_hcd and address 7
[ 3373.099534] usb 1-9: configuration #1 chosen from 1 choice
[ 3373.150880] usbcore: registered new interface driver libusual
[ 3373.161740] Initializing USB Mass Storage driver...
[ 3373.162059] scsi8 : SCSI emulation for USB Mass Storage devices
[ 3373.162346] usb-storage: device found at 7
[ 3373.162353] usb-storage: waiting for device to settle before scanning
[ 3373.162359] usbcore: registered new interface driver usb-storage
[ 3373.162363] USB Mass Storage support registered.
[ 3378.162520] usb-storage: device scan complete
[ 3378.169506] scsi 8:0:0:0: Direct-Access     Qualcomm MMC Storage      2.31 PQ: 0 ANSI: 2
[ 3378.180665] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 3378.180793] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 3381.401574] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3381.408556] sd 8:0:0:0: [sdc] Write Protect is off
[ 3381.408563] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3381.408565] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3381.423556] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3381.430553] sd 8:0:0:0: [sdc] Write Protect is off
[ 3381.430560] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3381.430562] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3381.430566]  sdc: sdc1
[ 3381.637550] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.637559] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.637564] end_request: I/O error, dev sdc, sector 1984000
[ 3381.637569] Buffer I/O error on device sdc, logical block 1984000
[ 3381.654551] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.654562] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.654568] end_request: I/O error, dev sdc, sector 1984000
[ 3381.654573] Buffer I/O error on device sdc, logical block 1984000
[ 3381.671548] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.671556] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.671561] end_request: I/O error, dev sdc, sector 1983992
[ 3381.671566] Buffer I/O error on device sdc, logical block 1983992
[ 3381.688548] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.688556] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.688560] end_request: I/O error, dev sdc, sector 1983993
[ 3381.688565] Buffer I/O error on device sdc, logical block 1983993
[ 3381.688568] Buffer I/O error on device sdc, logical block 1983994
[ 3381.688570] Buffer I/O error on device sdc, logical block 1983995
[ 3381.688573] Buffer I/O error on device sdc, logical block 1983996
[ 3381.688576] Buffer I/O error on device sdc, logical block 1983997
[ 3381.688579] Buffer I/O error on device sdc, logical block 1983998
[ 3381.688582] Buffer I/O error on device sdc, logical block 1983999
[ 3381.705550] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.705558] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.705563] end_request: I/O error, dev sdc, sector 1983992
[ 3381.722548] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.722556] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.722561] end_request: I/O error, dev sdc, sector 1983993
[ 3381.739549] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.739557] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.739562] end_request: I/O error, dev sdc, sector 1984000
[ 3381.756548] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.756555] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.756559] end_request: I/O error, dev sdc, sector 1984000
[ 3381.773556] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.773565] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.773570] end_request: I/O error, dev sdc, sector 1984000
[ 3381.790560] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.790570] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.790576] end_request: I/O error, dev sdc, sector 1983992
[ 3381.807550] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.807558] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.807563] end_request: I/O error, dev sdc, sector 1983936
[ 3381.824550] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.824557] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.824562] end_request: I/O error, dev sdc, sector 1983937
[ 3381.841569] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.841579] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.841584] end_request: I/O error, dev sdc, sector 1984000
[ 3381.858566] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.858578] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.858583] end_request: I/O error, dev sdc, sector 1984000
[ 3381.875555] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.875562] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.875567] end_request: I/O error, dev sdc, sector 96
[ 3381.892558] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.892565] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.892569] end_request: I/O error, dev sdc, sector 97
[ 3381.909554] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.909560] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.909564] end_request: I/O error, dev sdc, sector 96
[ 3381.926567] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.926574] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.926579] end_request: I/O error, dev sdc, sector 97
[ 3381.943555] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.943562] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.943567] end_request: I/O error, dev sdc, sector 96
[ 3381.960556] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.960563] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.960567] end_request: I/O error, dev sdc, sector 96
[ 3381.977554] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3381.977560] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3381.977565] end_request: I/O error, dev sdc, sector 97
[ 3382.866587] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3382.873593] sd 8:0:0:0: [sdc] Write Protect is off
[ 3382.873601] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3382.873603] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3382.888582] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3382.895595] sd 8:0:0:0: [sdc] Write Protect is off
[ 3382.895601] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3382.895603] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3382.895609]  sdc: sdc1
[ 3383.086575] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.086582] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.086587] end_request: I/O error, dev sdc, sector 1984000
[ 3383.103576] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.103583] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.103587] end_request: I/O error, dev sdc, sector 1984000
[ 3383.120577] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.120584] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.120588] end_request: I/O error, dev sdc, sector 1983992
[ 3383.137578] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.137585] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.137589] end_request: I/O error, dev sdc, sector 1983993
[ 3383.154585] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.154592] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.154596] end_request: I/O error, dev sdc, sector 1983992
[ 3383.171580] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.171587] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.171592] end_request: I/O error, dev sdc, sector 1983993
[ 3383.188576] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.188583] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.188587] end_request: I/O error, dev sdc, sector 1984000
[ 3383.205577] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.205583] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.205587] end_request: I/O error, dev sdc, sector 1984000
[ 3383.222586] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.222594] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.222598] end_request: I/O error, dev sdc, sector 1984000
[ 3383.239580] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.239587] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.239591] end_request: I/O error, dev sdc, sector 1983992
[ 3383.256579] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.256585] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.256590] end_request: I/O error, dev sdc, sector 1983936
[ 3383.273577] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.273583] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.273587] end_request: I/O error, dev sdc, sector 1983937
[ 3383.290582] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.290589] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.290594] end_request: I/O error, dev sdc, sector 1984000
[ 3383.307585] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.307592] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.307596] end_request: I/O error, dev sdc, sector 1984000
[ 3383.324579] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.324586] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.324590] end_request: I/O error, dev sdc, sector 96
[ 3383.341579] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.341585] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.341590] end_request: I/O error, dev sdc, sector 97
[ 3383.358583] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.358590] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.358595] end_request: I/O error, dev sdc, sector 96
[ 3383.375584] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.375591] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.375595] end_request: I/O error, dev sdc, sector 97
[ 3383.392585] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.392592] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.392596] end_request: I/O error, dev sdc, sector 96
[ 3383.409582] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.409588] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.409593] end_request: I/O error, dev sdc, sector 96
[ 3383.426585] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3383.426591] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3383.426596] end_request: I/O error, dev sdc, sector 97
[ 3384.865621] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3384.872621] sd 8:0:0:0: [sdc] Write Protect is off
[ 3384.872626] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3384.872629] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3384.887621] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3384.894622] sd 8:0:0:0: [sdc] Write Protect is off
[ 3384.894629] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3384.894633] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3384.894644]  sdc: sdc1
[ 3385.086614] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.086628] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.086635] end_request: I/O error, dev sdc, sector 1984000
[ 3385.103607] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.103614] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.103622] end_request: I/O error, dev sdc, sector 1984000
[ 3385.120610] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.120624] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.120632] end_request: I/O error, dev sdc, sector 1983992
[ 3385.137609] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.137621] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.137629] end_request: I/O error, dev sdc, sector 1983993
[ 3385.154608] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.154621] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.154628] end_request: I/O error, dev sdc, sector 1983992
[ 3385.171618] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.171632] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.171637] end_request: I/O error, dev sdc, sector 1983993
[ 3385.188611] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.188618] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.188625] end_request: I/O error, dev sdc, sector 1984000
[ 3385.205608] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.205620] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.205627] end_request: I/O error, dev sdc, sector 1984000
[ 3385.222610] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.222618] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.222624] end_request: I/O error, dev sdc, sector 1984000
[ 3385.239617] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.239625] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.239632] end_request: I/O error, dev sdc, sector 1983992
[ 3385.256616] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.256628] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.256636] end_request: I/O error, dev sdc, sector 1983936
[ 3385.273610] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.273622] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.273628] end_request: I/O error, dev sdc, sector 1983937
[ 3385.290611] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.290625] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.290633] end_request: I/O error, dev sdc, sector 1984000
[ 3385.307612] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.307619] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.307625] end_request: I/O error, dev sdc, sector 1984000
[ 3385.324612] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.324619] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.324625] end_request: I/O error, dev sdc, sector 96
[ 3385.341616] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.341629] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.341635] end_request: I/O error, dev sdc, sector 97
[ 3385.358624] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.358631] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.358636] end_request: I/O error, dev sdc, sector 96
[ 3385.375616] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.375622] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.375625] end_request: I/O error, dev sdc, sector 97
[ 3385.392617] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.392623] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.392626] end_request: I/O error, dev sdc, sector 96
[ 3385.409620] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.409625] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.409629] end_request: I/O error, dev sdc, sector 96
[ 3385.426618] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3385.426624] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3385.426627] end_request: I/O error, dev sdc, sector 97
[ 3386.868650] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3386.875652] sd 8:0:0:0: [sdc] Write Protect is off
[ 3386.875655] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3386.875658] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3386.890648] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3386.897646] sd 8:0:0:0: [sdc] Write Protect is off
[ 3386.897650] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3386.897652] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3386.898964]  sdc: sdc1
[ 3387.087649] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.087656] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.087661] end_request: I/O error, dev sdc, sector 1984000
[ 3387.087664] __ratelimit: 203 callbacks suppressed
[ 3387.087666] Buffer I/O error on device sdc, logical block 1984000
[ 3387.104646] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.104651] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.104655] end_request: I/O error, dev sdc, sector 1984000
[ 3387.104658] Buffer I/O error on device sdc, logical block 1984000
[ 3387.121653] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.121669] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.121674] end_request: I/O error, dev sdc, sector 1983992
[ 3387.121680] Buffer I/O error on device sdc, logical block 1983992
[ 3387.138650] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.138660] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.138668] end_request: I/O error, dev sdc, sector 1983993
[ 3387.138678] Buffer I/O error on device sdc, logical block 1983993
[ 3387.138681] Buffer I/O error on device sdc, logical block 1983994
[ 3387.138685] Buffer I/O error on device sdc, logical block 1983995
[ 3387.138687] Buffer I/O error on device sdc, logical block 1983996
[ 3387.138690] Buffer I/O error on device sdc, logical block 1983997
[ 3387.138693] Buffer I/O error on device sdc, logical block 1983998
[ 3387.138695] Buffer I/O error on device sdc, logical block 1983999
[ 3387.155649] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.155663] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.155668] end_request: I/O error, dev sdc, sector 1983992
[ 3387.172652] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.172666] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.172671] end_request: I/O error, dev sdc, sector 1983993
[ 3387.189651] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.189666] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.189671] end_request: I/O error, dev sdc, sector 1984000
[ 3387.206648] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.206664] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.206668] end_request: I/O error, dev sdc, sector 1984000
[ 3387.223658] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.223671] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.223679] end_request: I/O error, dev sdc, sector 1984000
[ 3387.240657] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.240671] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.240677] end_request: I/O error, dev sdc, sector 1983992
[ 3387.257655] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.257670] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.257676] end_request: I/O error, dev sdc, sector 1983993
[ 3387.274650] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.274663] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.274670] end_request: I/O error, dev sdc, sector 1983936
[ 3387.291646] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.291661] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.291666] end_request: I/O error, dev sdc, sector 1984000
[ 3387.308666] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.308683] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.308689] end_request: I/O error, dev sdc, sector 1984000
[ 3387.325652] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.325667] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.325672] end_request: I/O error, dev sdc, sector 96
[ 3387.342650] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.342659] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.342669] end_request: I/O error, dev sdc, sector 97
[ 3387.359648] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.359662] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.359667] end_request: I/O error, dev sdc, sector 96
[ 3387.376658] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.376673] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.376679] end_request: I/O error, dev sdc, sector 97
[ 3387.393661] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.393676] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.393681] end_request: I/O error, dev sdc, sector 96
[ 3387.410651] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.410664] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.410671] end_request: I/O error, dev sdc, sector 97
[ 3387.427649] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3387.427663] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3387.427668] end_request: I/O error, dev sdc, sector 96
[ 3388.869695] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3388.876694] sd 8:0:0:0: [sdc] Write Protect is off
[ 3388.876699] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3388.876701] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3388.891694] sd 8:0:0:0: [sdc] 1984001 512-byte hardware sectors (1016 MB)
[ 3388.898696] sd 8:0:0:0: [sdc] Write Protect is off
[ 3388.898701] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[ 3388.898703] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 3388.900021]  sdc: sdc1
[ 3389.095689] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.095704] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.095709] end_request: I/O error, dev sdc, sector 1984000
[ 3389.112702] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.112717] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.112722] end_request: I/O error, dev sdc, sector 1984000
[ 3389.129682] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.129696] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.129701] end_request: I/O error, dev sdc, sector 1983992
[ 3389.146679] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.146693] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.146698] end_request: I/O error, dev sdc, sector 1983993
[ 3389.163678] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.163691] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.163698] end_request: I/O error, dev sdc, sector 1983992
[ 3389.180690] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.180705] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.180713] end_request: I/O error, dev sdc, sector 1983993
[ 3389.197689] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.197704] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.197713] end_request: I/O error, dev sdc, sector 1984000
[ 3389.214684] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.214695] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.214699] end_request: I/O error, dev sdc, sector 1984000
[ 3389.231681] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.231695] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.231702] end_request: I/O error, dev sdc, sector 1984000
[ 3389.248713] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.248729] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.248740] end_request: I/O error, dev sdc, sector 1983992
[ 3389.265683] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.265697] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.265705] end_request: I/O error, dev sdc, sector 1983993
[ 3389.282684] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.282699] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.282704] end_request: I/O error, dev sdc, sector 1983936
[ 3389.299687] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.299702] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.299707] end_request: I/O error, dev sdc, sector 1984000
[ 3389.316686] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.316695] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.316704] end_request: I/O error, dev sdc, sector 1984000
[ 3389.333685] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.333700] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.333705] end_request: I/O error, dev sdc, sector 96
[ 3389.350686] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.350700] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.350705] end_request: I/O error, dev sdc, sector 97
[ 3389.367692] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.367706] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.367711] end_request: I/O error, dev sdc, sector 96
[ 3389.384697] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.384711] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.384716] end_request: I/O error, dev sdc, sector 97
[ 3389.401691] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.401705] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.401710] end_request: I/O error, dev sdc, sector 96
[ 3389.418682] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.418696] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.418701] end_request: I/O error, dev sdc, sector 97
[ 3389.435683] sd 8:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
[ 3389.435698] sd 8:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present
[ 3389.435703] end_request: I/O error, dev sdc, sector 96

```

---

### Post by jay li on 2008-12-22
Thanks sedawk for the correction, and yes I meant to repair. 
And as for you adlin5000, I meant on the same machine to do it and not on other like your room-mates.

---

### Post by adlin5000 on 2008-12-22
Ahh. Well this machine has never had windows on it so that would be kinda hard to do. :P

Also I did the "fdisk -l /dev/sdX" with sdc (I think thats where it was trying to put it) and got nothing. No errors no anything.

---

