---
title: "[Script] Mount Wubi Disk from Linux"
date: 2009-01-12
forum: General Help
---

### Post by Yashiro on 2009-01-12
Just posting this for people who are converting their wubi install to a dedicated partition with LVPM. Once done you may want to access your old setup in the event you modify something or whatever.

In the following examples you may need to edit some of the paths to match your system setup. *The following scripts assume your Windows partition is on /dev/sda1. *

Make a new text file:
```
#!/bin/sh
sudo mkdir -p /media/WindowsXP
echo "Mounting NTFS Partition"
sudo mount -t ntfs /dev/sda1 /media/WindowsXP
sleep 1
sudo mkdir -p /media/root.disk
echo "Mounting Wubi Disk"
sudo mount -o loop /media/WindowsXP/ubuntu/disks/root.disk /media/root.disk
sleep 1
echo "Done :)"
gksu nautilus /media/root.disk
exit 0 &
```
Save this as **mountwubi.sh**. Right click this new file, select Permissions tab and put a tick in the Execute box.

Create another text file:
```
#!/bin/sh
echo "Unmounting Wubi Disk"
sudo umount /media/root.disk
sleep 1
echo "Unmounting NTFS Partition"
sudo umount /media/WindowsXP
sleep 1
echo "Done :)"
exit 0 &
 
```
Save this as **umountwubi.sh**. Right click this new file, select Permissions tab and put a tick in the Execute box.


Double clicking **mountwubi.sh** and selecting Run in Terminal will mount your old wubi install and open a root nautilus for full access to the files.
The function of **umountwubi.sh** is pretty obvious :)

---

### Post by 60hbe16es52 on 2009-01-12
is [jordan shoes](http://www.smkings.com) good enough for play basketball?

---

### Post by Aaron.A on 2009-07-05
sorry to bump this old thread, 
but, does this assume ubuntu is installed to C:\Ubuntu (default) ?
and, can i simply copy *everything* from the disk and paste it
into my file system, reboot, and magically have my system exactly 
as my wubi was? 

lol can i, can i, pleasssse?

---

### Post by earthpigg on 2009-07-05
> **Aaron.A said:**
> sorry to bump this old thread, 
but, does this assume ubuntu is installed to C:\Ubuntu (default) ?
and, can i simply copy *everything* from the disk and paste it
into my file system, reboot, and magically have my system exactly 
as my wubi was? 

lol can i, can i, pleasssse?

nope.

but you can copy all the hidden files/folders from your old home into/over the ones in your new home.

the .mozilla directory in /home, for example, has all your firefox bookmarks, settings, etc

---

### Post by Aaron.A on 2009-07-06
> **earthpigg said:**
> nope.

but you can copy all the hidden files/folders from your old home into/over the ones in your new home.

the .firefox directory in /home, for example, has all your firefox bookmarks, settings, etc

thanks a lot mate :D
i only had to modify sda1 to sda2 so no problems there. 
i'm moving the files now.

---

### Post by manicmoddin on 2010-04-11
Just gotta say thanks for this, been spending a lot of time looking for an answer like this...

It never occured to me to mount the NTFS partition first

Many thanks

Jimmy

---

### Post by goodtimetribe on 2011-01-07
just another note to say thank you :)

---

### Post by chaware on 2011-01-07
Thank you very much. I had lot of struggle trying to do this and the answer is simple!

---

### Post by Anxituh on 2011-10-17
:popcorn: ;) Sorry for interrupting.. How can i use my root.disk file (or entire C:\ubuntu\ folder) from a WUBI installation to replace entirely for the same version of UBUNTU installed on a different partition inside the same drive as C:\?? REASON: i'm tired of using the root.disk (WUBI install) because UBUNTU has become too slow as Windows (C:\) has that fragmentation handicap.... So, i installed a fresh UBUNTU of the same version on a partition inside the same drive with live CD but i don't wanna configure all again and just thought of mounting entire root.disk file on the partition of new UBUNTU and replace all files if needed. IS that possible? I know i have to change a bit the grub.cfg file for booting questions. CAN this be DONE this way?? THANKS my friends!

---

