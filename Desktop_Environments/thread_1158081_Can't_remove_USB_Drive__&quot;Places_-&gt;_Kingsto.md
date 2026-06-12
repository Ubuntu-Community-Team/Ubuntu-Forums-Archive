---
title: "Can't remove USB Drive  &quot;Places -&gt; Kingston&quot;"
date: 2009-05-13
forum: Desktop Environments
---

### Post by LarryJ2 on 2009-05-13
The part of gnome/ubuntu that automatically mounts my KINGSTON brand USB thumb drives has become hopeless confused.  I have a persistent  entry  in Places that reads "KINGSTON".   When I right click on it, I do not receive an unmount prompt. Instead, nautilus file browser opens.  When I then try to create a folder there, I get an error window "Error while creating directory untitled folder.  There was an error creating the directory in /media/KINGSTON.  Error removing file: Input/output error" This entry persists regardless whether I have a KINGSTON usb thumb drive plugged in or not.  

1. There's nothing in /etc/fstab that mounts  usb drives.

2. mount  shows:  
> /dev/sdf1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

and that never changes whether the drive is plugged in or not.  But this appears to be only a label.  No writable storage ever appears in back of (mounted to) /media/KINGSTON.

3. If I bring nautilus up on /media/KINGSTON and try to create a folder, I get the same message described above (Error creating Directory...)

4.  When I try to create a folder (as in 3 above) dmesg shows this out:
> [967105.694094] FAT: Directory bread(block 15344) failed
[967105.694100] FAT: Directory bread(block 15345) failed
[967105.694103] FAT: Directory bread(block 15346) failed
[967105.694105] FAT: Directory bread(block 15347) failed
[967105.694108] FAT: Directory bread(block 15348) failed
[967105.694111] FAT: Directory bread(block 15349) failed
[967105.694114] FAT: Directory bread(block 15350) failed
[967105.694117] FAT: Directory bread(block 15351) failed
[967112.792907] FAT: Directory bread(block 15344) failed
[967112.792913] FAT: Directory bread(block 15345) failed
[967112.792916] FAT: Directory bread(block 15346) failed
[967112.792919] FAT: Directory bread(block 15347) failed
[967112.792921] FAT: Directory bread(block 15348) failed
[967112.792924] FAT: Directory bread(block 15349) failed
[967112.792927] FAT: Directory bread(block 15350) failed
[967112.792930] FAT: Directory bread(block 15351) failed
[967112.792936] FAT: FAT read failed (blocknr 1196)

5. With no drive plugged in but the Places -> KINGSTON entry still showing in the menu,  lsusb shows no KINGSTON:
> Bus 008 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:2220 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
The Canon, INc is a USB Scanner and  the Realtek is a 3.5 inch memory card reader attached as usb device.

6.  I should add that the KINGSTON entry in Places is not a Nautilus book mark.  It appears above the bookmark entries.   See screen shot attached.


At this point,  I'd be happy just to get back the defaults. Namely,  I plug in the usb drive,  an ICON appears on the desktop,  I click on the icon and nautilus shows my files.

Larry

---

### Post by LarryJ2 on 2009-05-13
Sometimes the blind and humble have all the luck...

1. Plug in your USB Drive

2.  sudo  gconf-editor.

3.  Click down to  System -> Storage -> Volumes

4.  I see an entry "_org_freedesktop_Hal_devices_volume_uuid_3433_3231

5.  High light that entry (yours may be different since you probably don't have a KINGSTON identical to mine.

6.  In the right side pane, right  click on mount point.

7.  Select Edit Keys

8.  If the Value entry is something containing a slash "/"  such as
/media/KINGSTON,  or /media/LJ  as mine did, change it to just one
word.  For example
Value:  KINGSTON-LJ
thereby getting rid of the slashes.

9. Exit the gconf-editor, unplug and plugin again your usbdrive,  and then look under  /media to see if the usb drive got mounted.   Mine shows up under /media/KINGSTON-LJ

10. When you plug in the USB drive,  you should see an entry in the Places Menu appear.   Mine shows "KINGSTON"

11.  If I click on KINGSTON, I shortly see a tool tip pop-up which says "Mount KINGSTON",  I click on it and then see a KINGSTON icon appear on the gnome desktop  and my files appear under /media/KINGSTON-LJ

Whew....:D

Larry

---

