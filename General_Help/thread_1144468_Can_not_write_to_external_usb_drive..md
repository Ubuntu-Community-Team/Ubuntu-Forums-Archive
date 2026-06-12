---
title: "Can not write to external usb drive."
date: 2009-04-30
forum: General Help
---

### Post by gloken on 2009-04-30
Hi, I'm running a box with a fresh install of 9.04 on it. I have an external USB drive for backup purposes.  Ubuntu is detecting the drive and mounting it as /media/Backup Drive and although I have a desktop icon and can browse the drive, it will not allow me to write the drive.

How can I add write permissions to the drive?
Thanks in advance.

---

### Post by taurus on 2009-04-30
What filesystem is that external drive?

```
sudo fdisk -l
```

---

### Post by gloken on 2009-04-30
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb24db24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29650   238163593+  83  Linux
/dev/sda2           29651       30401     6032407+   5  Extended
/dev/sda5           29651       30401     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b41c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

---

### Post by gloken on 2009-05-01
The drive is sdb, so it should be a proper linux filesystem.

---

### Post by taurus on 2009-05-01
You just need to change the ownership of the mount point, /media/Backup Drive, from root to your login name so you can write to it anytime you want.  _Assuming_ your login name is loken, try

```
sudo chown -R loken:loken /media/"Backup Drive"
ls -la /media
```

---

### Post by gloken on 2009-05-01
Interesting. Give me a few years and I'll have this OS figured out.
Thanks!

---

### Post by pwab on 2009-05-04
This is actually a sub-optimal solution... If this person's problem was anything like mine the solution is something like the following...

If you are using gnome, then gnome is responsible for letting the automounter know what the mount options must be for any flash disk that is plugged into the system. (Presumably KDE does something similar)

Open gconf-editor (or gksudo gconf-editor) via the Alt-F2 app starter and open the System/Storage/default_options tree. Find the type of filesystem that the USB device has. (Probably vfat or NTFS-3G) and set the mount options in there. If I were you, I'd set this as a default setting via the root instance of gconf-editor.

I added uid= and gid=users. 'uid=' makes the current logged in user the owner of the mounted file system and 'gid=users' sets the group owner of the mounted volume. I created the users group on my system and my wife and I belong to that group. That means she can mount it (and become the owner of the mounted volume) I can log in and still write to the filesystem since we both belong to the same user group.

---

### Post by johnaaronrose on 2009-05-06
I've previously formatted the usb disk as fat32 (one fat32 partition only). I set the user ids in Users & Groups for group users. I then did Alt&F2 and gconf-editor and gid=users entered under system/storage/vfat. However, when I connect the usb drive, a window is displayed stating that invalid mount option. Any ideas?

PS I'm using jaunty.

---

### Post by johnaaronrose on 2009-05-06
Just found an archived thread. Solution is:
with root permissions open the file  
/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi

in the file find this section :  <!-- allow these mount options for vfat -->

and add this line : <append key="volume.mount.valid_options"
type="strlist">gid=</append>

example :

<!-- allow these mount options for vfat -->
&#8722;
<match key="volume.fstype" string="vfat">
&#8722;
<match key="/org/freedesktop/Hal/devices/computer:system.kernel.name"
string="Linux">
<append key="volume.mount.valid_options" type="strlist">utf8</append>
<append key="volume.mount.valid_options" type="strlist">shortname=</append>
<append key="volume.mount.valid_options" type="strlist">codepage=</append>
<append key="volume.mount.valid_options" type="strlist">iocharset=</append>
<append key="volume.mount.valid_options" type="strlist">umask=</append>
<append key="volume.mount.valid_options" type="strlist">dmask=</append>
<append key="volume.mount.valid_options" type="strlist">fmask=</append>
<append key="volume.mount.valid_options" type="strlist">uid=</append>
<append key="volume.mount.valid_options" type="strlist">gid=</append>
<append key="volume.mount.valid_options" type="strlist">flush</append>

when it's done save and close. 

PS advisable to change using gconf-editor umask=007 (from umask=777). 
Do this for each user in the users group (i.e. each user who has gconf-editor also add gid=users).

---

