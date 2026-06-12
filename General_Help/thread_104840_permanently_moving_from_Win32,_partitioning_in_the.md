---
title: "permanently moving from Win32, partitioning in the way"
date: 2005-12-17
forum: General Help
---

### Post by ajmoncrief on 2005-12-17
Hey guys, I am currently running a dual-boot with XP and have finally gotten Breezy to work properly (multimedia, web-browsing, printing, scanning etc.)  I was wondering if someone could point me in the right direction for taking windows completely off of my computer (safely preserving ubuntu in the meanwhile) and dedicating the entire hard drive to ubuntu.  Brief info on /dev/hda (120GB total) is attached below:

Thanks in advance for the help.

---

### Post by GreyFox503 on 2005-12-17
EDIT:  Make sure you unmount any filesytem before changing/formatting it!

If you just want free up the 90GB that XP is using, you can just use qtparted to format /dev/hda1 with a new filesystem like ext3 or reiserfs (my fave).  There's nothing more to be done uninstalling it, except maybe editing your /boot/grub/menu.lst to clear out the entry for XP.

If you're talking about rearranging your partitions to move Ubuntu to the front, I'm not sure if qtparted does stuff like that, Partition Magic style.

---

### Post by ajmoncrief on 2005-12-17
[QUOTE=GreyFox503]EDIT:  Make sure you unmount any filesytem before changing/formatting it!

If you just want free up the 90GB that XP is using, you can just use qtparted to format /dev/hda1 with a new filesystem like ext3 or reiserfs (my fave).  There's nothing more to be done uninstalling it, except maybe editing your /boot/grub/menu.lst to clear out the entry for XP.

If you're talking about rearranging your partitions to move Ubuntu to the front, I'm not sure if qtparted does stuff like that, Partition Magic style.[/QUOTE]

Thanks, for the reply I will probably just use my knoppix 4 live dvd.  In any event, I failed to mention grub is not mounted on the mbr, but on the actual linux partition itself. (hda2).  Will this matter?  

Also, if I just convert the other partitions (minus the swap of course) into ext3, will they be directly accesible in Breezy?  Or will I have to point my prog to the new path in order to save/open stuff?  Im not sure if  I am technically presenting this the correct way or not, but what I am getting at is will I be able to go to my user home directory (which is on hda2) and directly use the space that was once allocated to hda1; or will I have to split usage between the partitions?

---

### Post by GreyFox503 on 2005-12-17
If you just reformat your NTFS partition into ext3, then GRUB should function in the same way.  If you installed grub to your hard drive, then the MBR points the second-stage boot loader on your Ubuntu partitition, /dev/hda2.  If you change the location of this partition or your Ubuntu installation, then you would have to change GRUB to compensate.

I would leave hda3 and hda5 alone, because that's your swap partition.

And when you use this new partition, it will not be automatically added to your home directory.  Your home is probably on hda2.  When you mount the new hda1, you'll have to choose where you want it to be.  I'd recommend mounting it in /mnt/hda1 or something, and then if you want, you can make a symbolic link to it inside your home directory, something like /home/username/hda1  ->  /mnt/hda1.

There is another option if you really want it.  I believe it is possible to move your /home directory permanently to a different location, in this case hda1.  It is easiest to do this during the installation process, but you can do afterwards also.  I'm not experienced on how to do that.

This guy's post looks like a good place to start if you're interested:
[http://www.ubuntuforums.org/showthread.php?t=46866]("http://www.ubuntuforums.org/showthread.php?t=46866")


BTW, I love Knoppix.  It's great for this kind of stuff, and good to have around.

---

