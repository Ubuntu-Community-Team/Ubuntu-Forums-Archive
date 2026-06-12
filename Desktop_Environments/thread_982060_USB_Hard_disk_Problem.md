---
title: "USB Hard disk Problem"
date: 2008-11-14
forum: Desktop Environments
---

### Post by neon100 on 2008-11-14
I have a 60GB USB Hard drive that remains connected all the time. When i hibernate and then turn back on, then there appears another icon of that USB HD. The previous icon cannot be 'unmounted' and cannot be deleted either. So soon my desktop gets full of over 6 icons of the same HD and sometimes i forget which icon is the newest one and try each one of them before finding the correct icon. 

But when i reboot, the problem is solved. F1 !

using 7.04.

---

### Post by neon100 on 2008-11-15
should i assume that no one knows the answer?

---

### Post by quirks on 2009-06-20
Sorry for reviving such an old thread, but I forgot to answer, when I found the solution. I used to have the same problem and here is how I fixed it (others finding this thread might want to know, too):

The problem is that the disk does not get unmounted when you hibernate. This is actually pretty bad, since it may corrupt the data on your disk, because when the computer hibernates, it does not unmount the filesystem cleanly. To unmount it automatically on hibernation, do this:

1. Find out the ID of your external USB disk:
```
ls -l /dev/disk/by-id
```
The output looks similar to this:
```
total 0
lrwxrwxrwx 1 root root  9 2009-06-13 22:59 ata-SAMSUNG_HM160HI_S18PJD0PB63192 -> ../../sda
lrwxrwxrwx 1 root root 10 2009-06-13 22:59 ata-SAMSUNG_HM160HI_S18PJD0PB63192-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-06-13 22:59 ata-SAMSUNG_HM160HI_S18PJD0PB63192-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-06-13 22:59 ata-SAMSUNG_HM160HI_S18PJD0PB63192-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-06-13 22:59 ata-SAMSUNG_HM160HI_S18PJD0PB63192-part4 -> ../../sda4
lrwxrwxrwx 1 root root  9 2009-06-13 22:59 scsi-1ATA_SAMSUNG_HM160HI_S18PJD0PB63192 -> ../../sda
lrwxrwxrwx 1 root root 10 2009-06-13 22:59 scsi-1ATA_SAMSUNG_HM160HI_S18PJD0PB63192-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-06-13 22:59 scsi-1ATA_SAMSUNG_HM160HI_S18PJD0PB63192-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-06-13 22:59 scsi-1ATA_SAMSUNG_HM160HI_S18PJD0PB63192-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-06-13 22:59 scsi-1ATA_SAMSUNG_HM160HI_S18PJD0PB63192-part4 -> ../../sda4
lrwxrwxrwx 1 root root  9 2009-06-20 21:13 [COLOR="Red"]usb-Myson_Century__Inc._USB_Mass_Storage_Device_100[/COLOR] -> ../../sdb
lrwxrwxrwx 1 root root 10 2009-06-20 21:13 usb-Myson_Century__Inc._USB_Mass_Storage_Device_100-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-06-20 21:13 usb-Myson_Century__Inc._USB_Mass_Storage_Device_100-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2009-06-20 21:13 usb-Myson_Century__Inc._USB_Mass_Storage_Device_100-part5 -> ../../sdb5
```
Mine is named **usb-Myson_Century__Inc._USB_Mass_Storage_Device_100**. Yours probably has got **usb** somewhere in its name, too. If you are not sure which one it is. Just unmount and unplug the disk and re-run the command, to see which one disappeared. Make sure, you pick the disk ID which does not end on **-partX**!

2. Create a script in **/etc/pm/sleep.d** using nano (or any other plain text editor of your choice). You must run it as root:
```
sudo nano /etc/pm/sleep.d/50-unmount-usb-disk.sh
```
3. Paste this code in it:
```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
        hibernate)
                # set this variable to the ID of your disk
                DISK_ID="usb-Myson_Century__Inc._USB_Mass_Storage_Device_100"

                # check if USB disk is plugged in
                if [ -e "/dev/disk/by-id/$DISK_ID" ]; then

                        # determine device file of USB disk (i.e., destination of symlink in /dev/disk/by-id)
                        DEVICE_FILE=`ls -l "/dev/disk/by-id/$DISK_ID" | grep -o -E '.{3}$'`

                        # find all partitions of the disk which are currently mounted
                        MOUNTED_FILESYSTEMS=`mount | grep /dev/$DEVICE_FILE | awk '{print $1}'`

                        # terminate all processes accessing any of the partitions on the disk
                        fuser -k -TERM -m $MOUNTED_FILESYSTEMS

                        # give processes a few seconds to terminate, then kill all remaining ones the hard way
                        sleep 3

                        # kill all processes accessing any of the partitions on the disk
                        fuser -k -KILL -m $MOUNTED_FILESYSTEMS

                        umount $MOUNTED_FILESYSTEMS

                        # in case unmounting failed, at least flush the disk buffer cache
                        [ $? -ne 0 ] && sync
                fi
        ;;

        *)
        ;;
esac

exit
```
4. On line 8, change the value of the variable **DISK_ID** to the ID you found out in step #1. But make sure you don't screw up the double quotes!

5. Save and close nano by pressing **Ctrl-X**, then **y**.

6. Make the script executable:
```
sudo chmod a+x /etc/pm/sleep.d/50-unmount-usb-disk.sh
```
7. Test it by hibernating and resuming.

I hope I could help some people!

EDIT: This was tested on Hardy. I have not tested it on any newer or older releases of Ubuntu.

---

