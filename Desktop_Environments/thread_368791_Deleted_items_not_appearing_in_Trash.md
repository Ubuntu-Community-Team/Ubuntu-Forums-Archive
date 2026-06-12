---
title: "Deleted items not appearing in Trash"
date: 2007-02-23
forum: Desktop Environments
---

### Post by badbobbybarnes on 2007-02-23
I'm using Edgy 6.10, and have a problem when deleting files. Even if I right-click "Move To Trash" or drag and drop them onto the trash icon, they just disappear! The Trash applet says "No Items In Trash".... but they DO exist in my /home/.Trash hidden folder. I've read a similar post and tried mounting the drives with a UUID, but it makes no difference. Here's my fstab file:

[COLOR="Blue"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
UUID=9956d5ab-aa83-49b3-bb5e-046478518181       /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=9956d5ab-aa83-49b3-bb5e-046478518181 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0[/COLOR]

That's the limit of my Linux skills I'm afraid. Anyone got any ideas? Thanks

---

### Post by phossal on 2007-02-23
Did it ever work? Ever? Perhaps it's as simple as removing and replacing the applet? Perhaps permissions on a file or folder are screwed up?

---

### Post by shareMenaPeace on 2007-02-23
Did you tried when you in trash window to press "CTRL + H" to see hidden files?

---

### Post by badbobbybarnes on 2007-02-24
As far as I can remember, it worked fine when I had 6.06 installed, but has never worked with 6.10. I even recently wiped my hard drive and reinstalled 6.10 again from scratch, but it still didn't work. I've also tried viewing the hidden files in the Trash window, but it says there aren't any.

So I still need some help on this. Do you guys know if can I get assistance from anyone at Ubuntnu, and if so how/where? Thanks.

---

### Post by haricharan on 2007-02-24
Check in Configuration editor if /apps/nautilus/preferences/enable_delete is checked. If its checked, remove the check and try delete some file......I am not sure if this would work out.....just try and see

---

### Post by badbobbybarnes on 2007-02-24
Just checked that, but enable_delete is already un-checked, I'm afraid.

Further update. I wiped everything again and reinstalled 6.06 - same problem, so it's not just 6.10. Then I wiped everything again and ran 6.10 directly from the Live CD, and tried moving a file to trash from there. Same problem: the deleted file didn't appear in the Trash window but is in the hidden .Trash folder. I've also noticed that when right-clicking on a file and selecting Move To Trash, no confirmation box appears, even though the confirm_trash option is checked in config editor.

Any more ideas please?

---

### Post by haricharan on 2007-02-24
have u installed ntfs-3g??....if so deleting files from ntfs partition would go into .Trash and not in Trash.... Trash doesnt have any filesystem linked to it..so files from ntfs and fat would go into .Trash....

---

### Post by badbobbybarnes on 2007-02-24
No, ntfs-3g is not installed, and these are linux partitions, not NTFS.

---

### Post by badbobbybarnes on 2007-02-24
... but there ARE some unmounted NTFS partitions: /dev/hda1 and /dev/hda5 on hard disk 1 (the only partitions on that one), and /dev/hdb1 on hard disk 2 - the same drive as the linux partitions /dev/hdb2 and /dev/hdb5. Could this be anything to do with the problem?

---

### Post by haricharan on 2007-02-24
the problem looks weird.....lets see if someone else posts some suggestions...sorry i couldnt help further...i m a learner too!!

---

### Post by TrentRose on 2007-03-10
I can only contribute to this conversation by adding that my system also exhibits this exact behaviour.  It's a brand new install and I've also tried all suggestions without resolution.

---

### Post by HardcoreLinux on 2007-03-17
I have this problem today too.  It started doing it right after I installed e17 and engage don't know what it is.

---

### Post by hackle577 on 2007-05-03
I am having the same problem now with Feisty, but I think it has something to do with .Trash folders being created on external drives. From what I've read, a .Trash folder is created there that the trash applet points to, but when you eject the drive, it never points back to your regular trash directory.

[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/34247)

---

### Post by wild_oscar on 2007-11-30
> **haricharan said:**
> have u installed ntfs-3g??....if so deleting files from ntfs partition would go into .Trash and not in Trash.... Trash doesnt have any filesystem linked to it..so files from ntfs and fat would go into .Trash....

Is it possible to make the Trash (ie, "deleted items" or trash icon) display the contents of the .Trash-user folders of the different disks then?

---

