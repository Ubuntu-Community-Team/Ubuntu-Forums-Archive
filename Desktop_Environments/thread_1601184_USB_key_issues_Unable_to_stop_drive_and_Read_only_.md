---
title: "USB key issues: Unable to stop drive and Read only file system"
date: 2010-10-19
forum: Desktop Environments
---

### Post by adummy on 2010-10-19
Every time when I right click the USB drive icon and select "Safely remove drive" I always get this error message```
**Unable to stop drive**

Error detaching: helper exited with exit code 1: Detaching device /dev/sdc
USB device: /sys/devices/pci0000:00/0000:00:04.1/usb2/2-4)
SYNCHRONIZE CACHE: synchronize cache(10):  Fixed format, current;  Sense key: Key=9
 Additional sense: Logical unit not ready, cause not reportable
  Info fld=0x0 [0] 
FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
```
even though the icon does disappear from the desk top. :confused:
I have been ignoring it since the USB drive seems working fine.

Now I have a more serious problem. When I tried to copy files onto the USB drive it says "read only file system" and doesn't let me. I tried unplug and plug the USB key but that doesn't help. :(

---

### Post by mikewhatever on 2010-10-19
When was the last time you've run a file system check on it? Do you know what file system is there? 
Can you post the output of **sudo fdisk -l** with the device attached.

---

### Post by adummy on 2010-10-19
> **mikewhatever said:**
> When was the last time you've run a file system check on it? Do you know what file system is there? 
Can you post the output of **sudo fdisk -l** with the device attached.

Here you go:
```
last_lba(): I don't know how to handle files with mode 40700
```File system is FAT32 - is this compatible with ubuntu?

Windows **chkdsk** did find a bunch of errors and fixed them with **/f** option. After the fix the ubuntu **fdisk** still gives the same "I don't know" message and "safely remove disk" still gives the error message. Help!

---

### Post by mikewhatever on 2010-10-20
If the file system check doesn't solve it, formatting may help. Just backup the files before formatting. Both fat32 and ntfs, Windows file systems, work in Linux.

---

### Post by adummy on 2010-10-20
> **mikewhatever said:**
> If the file system check doesn't solve it, formatting may help. Just backup the files before formatting. Both fat32 and ntfs, Windows file systems, work in Linux.

Thanks but I would avoid formatting if possible though. It works fine on Windows PCs. I just did chkdsk two more time, both OK. I copied and binary compared some files in between the two, all OK. Safely removed from the Windows PC no problem. Any other suggestions to check on the ubuntu side?

---

### Post by michopop on 2010-12-25
the same problem on nokia 5230 with a 16 gb sd card! any other solution then formating?

---

