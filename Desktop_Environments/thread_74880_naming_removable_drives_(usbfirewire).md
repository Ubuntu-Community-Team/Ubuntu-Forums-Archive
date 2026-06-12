---
title: "naming removable drives (usb/firewire)"
date: 2005-10-12
forum: Desktop Environments
---

### Post by relarson on 2005-10-12
Hi I'm trying to figure out how to name partitions on my removable firewire/usb drives.  Whenever I plug it in the partitions mount as  /media/ieee1394disk, /media/ieee1394disk-1, and  /media/ieee1394disk-2, which would be ok except that each time I reboot or remount the drive the partitions don't stay the same!  

In other words sometimes partition 1 is /media/ieeee1394disk and other times it shows up as ieee1394disk-1 or 2, so is there some way to force partition 1 to be ieeedisk, partition 2 to ieeedisk-2, and partition 3 to be ieeedisk-3 on every boot/mount?


Thanks for any help or pointers to more information about this!
-Rich

---

### Post by 11hjpphty76lkjj on 2005-10-12
Not sure if this helps..but you may be able to edit the fstab file and specificly put a part in there for your removeable drive.  So you do something like this:

umount the drive
terminal
sudo rmdir  /media/ieee1394disk, 
sudo rmdir /media/ieee1394disk-1
sudo rmdir /media/ieee1394disk-2
sudo mkdir /media/<cool name of usb drive here>
sudo gedit /etc/fstab
put a line in there something like this:
/dev/sda1 /media/<cool name of usb drive here> vfat rw,auto   0    0

note: where it says vfat is where you put the format type.  ie, ext2, ext3, reiserfs, etc. also where is says /dev/sda1 is where you put the usb drive path.  could be different for your system, device, and what not.

I'm plucking this right out of my head so I could have the syntax incorrect someplace.

save, close in terminal then type mount -a

You may need to adjust the permissions as well, and you'll need to do that with the drive umounted.  chmod 777 /media/<cool name of usb drive here>

Like I said, can't say this will fix it..but it seems like it might.  Sorry if I got anything incorrect.

Aaron

---

### Post by relarson on 2005-10-13
Thanks, but what I'm really trying to find out is how to do that using the new automount type stuff, which  I believe is controlled by HAL or perhaps something with pmount?  ... so for example I just plug in my usb or firewire drive, how do I tell it to automatically mount a particular drive as a particular name not just on boot but at any time that I plug in the drive.

Thanks!
-Rich

---

### Post by kiddo on 2005-10-16
Same problem here! It worked in hoary (the position of my usb backup partitions were remembered) but now it's random.

My rsync backup script depends on this, any idea how we could fix that without plunging into fstab?

---

### Post by dlai on 2005-11-16
Hey everybody, there must be some news to this, i would really like to have my usb drive mounting at the same mountpoint everytime...

---

### Post by dlai on 2005-11-18
I made a how to, hope it helps: 

[http://ubuntuforums.org/showthread.php?p=502098#post502098](http://ubuntuforums.org/showthread.php?p=502098#post502098)

---

### Post by relarson on 2005-12-18
Thanks!
I finally got back to checking on this thread after I had figured out how to do it myself, for anyone else here is what I did, though check out the above mentioned How-to for a better description of editing the fdi files.


The easiest way to do this, if your filesystem is ext* is to set the volume label using tune2fs -L "the_name_you_want" /dev/<device name>  

so for me:

tune2fs -L "fire-2" /dev/sda2

means that when I plug in my firewire drive, the partition on /dev/sda2 is mounted as /media/fire-2.

If you are not using a filesystem that supports labels you will have to do as previous posters have described, editing the fdi/policy/10osvendor/10-storage-policy.fdi


for my vfat partition I did the following:
in the section like this:
  <!-- Normal volumes; use volume label, uuid or drive_type -->
    <match key="block.is_volume" bool="true">
      <match key="volume.fsusage" string="filesystem">
        <!-- skip for drives with the no partitions hint (they are handled above) -->
        <match key="@block.storage_device:storage.no_partitions_hint" bool="true">
          <merge key="volume.policy.desired_mount_point" type="copy_property">@block.storage_device:storage.policy.desired_mount_point</merge>
        </match>
        <match key="@block.storage_device:storage.no_partitions_hint" bool="false">

..... Added section below.....

         <!-- for my vfat firewire drive set it to fire-1 -->
          <match key="volume.uuid" string="42AC-D677">
                <merge key="volume.policy.desired_mount_point" type="string">fire-1</merge>
                <match  key="volume.label" empty="true">
                        <!-- for my vfat firewire drive set its desktop (volume name) to fire-1 also -->
                        <merge key="volume.label" type="string">fire-1</merge>
                </match>
          </match>
.... end added section ....

To find what the UUID of your drive is go to System menu-> Administration->Device Manager (Hal)
then select your volume and look at the advanced tab for the volume.uuid, probably at the end of the list.

Hope that helps someone!
-Rich

---

