---
title: "can not figure out to auto mount partition"
date: 2009-01-17
forum: General Help
---

### Post by -jay- on 2009-01-17
here is my fstab where do i ad the line to auto mount my 1 partition

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c62656ec-4268-4baf-a6d1-8dd31f7bc52a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=3b89a995-53ff-4d8c-8f34-61abc60fc25e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by mikewhatever on 2009-01-17
Well, it doesn't matter, usually, the bottom of the file is the easiest, because it needs less text editing.

---

### Post by -jay- on 2009-01-17
ok cool what would be the code to allow permission i don't want to mess things up sorry noob here

---

### Post by mikewhatever on 2009-01-17
Can you post the output of <sudo fdisk -l>.

---

### Post by drs305 on 2009-01-17
You will also want to run the following to get the UUID of the partition. UUIDs will not change the way the /dev/sdXX designations can, so UUID identification is becoming the standard.

```
sudo blkid -c /dev/null

```

If you also give us your proposed mountpoint (such as /media/mydata) we can create the line for you.

Or you can learn about fstab for yourself by looking at this link:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by -jay- on 2009-01-17
> **mikewhatever said:**
> Can you post the output of <sudo fdisk -l>.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45e845e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18752   150625408+  83  Linux
/dev/sda2           18753       30401    93570592+   5  Extended
/dev/sda5           30104       30401     2393685   82  Linux swap / Solaris
/dev/sda6           18753       29635    87417634+  83  Linux
/dev/sda7           29636       30102     3751146   82  Linux swap / Solaris

and

/dev/sda1: LABEL="Beta" UUID="06ba37c5-4b9c-431e-9b5b-02bcd510d747" TYPE="ext3"  <<< this is what i want to be auto mounted
/dev/sda5: UUID="3613f4da-9269-45ad-a5ba-9a509bb8f8a9" TYPE="swap" 
/dev/sda6: UUID="c62656ec-4268-4baf-a6d1-8dd31f7bc52a" TYPE="ext3" 
/dev/sda7: UUID="3b89a995-53ff-4d8c-8f34-61abc60fc25e" TYPE="swap"

---

### Post by drs305 on 2009-01-17
Backup fstab and open for editing (I use gedit in the example but you can use another text editor if you wish):
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Add this line at the bottom of fstab, then save the file:
```

UUID=06ba37c5-4b9c-431e-9b5b-02bcd510d747 /media/Beta ext3 defaults,users 0 2

```

Make sure the mountpoint /media/Beta exists (or whatever you want the mountpoint name to be):
```

sudo mkdir /media/Beta
sudo chown -R *[COLOR="DarkRed"]yourusername:yourusername[/COLOR]* /media/Beta
chmod -R 755 /media/Beta    # read/write/execute for you, read/execute for group and others.

```

Mount the device:
```

sudo umount /dev/sda1  # unmount if previously mounted
sudo mount /dev/sda1    # You should be able to mount it without 'sudo' if you included the '*users'* option included above.

```
If nothing appears to happen, it successfully mounted.

---

### Post by -jay- on 2009-01-17
ok im stuck on this part i get the following

jay@jay-desktop:~$ sudo mkdir /media/Beta
mkdir: cannot create directory `/media/Beta': File exists
jay@jay-desktop:~$ sudo chown -R jay:jay /media/Beta
jay@jay-desktop:~$ chmod -R 755 /media/Beta/read/write/execute
chmod: cannot access `/media/Beta/read/write/execute': No such file or directory
jay@jay-desktop:~$

---

### Post by drs305 on 2009-01-17
> **-jay- said:**
> ok im stuck on this part i get the following

jay@jay-desktop:~$ sudo mkdir /media/Beta
mkdir: cannot create directory `/media/Beta': File exists
jay@jay-desktop:~$ sudo chown -R jay:jay /media/Beta
jay@jay-desktop:~$ chmod -R 755 /media/Beta/read/write/execute
chmod: cannot access `/media/Beta/read/write/execute': No such file or directory
jay@jay-desktop:~$

The folder Beta already exists. This is good.
The second command should not include the comments.
```

chmod -R 755 /media/Beta

```

---

### Post by -jay- on 2009-01-17
ok im getting to it but now get this

jay@jay-desktop:~$ sudo chown -R jay:jay /media/Beta
jay@jay-desktop:~$ chmod -R 755 /media/Beta
jay@jay-desktop:~$ sudo mount /dev/sda1
mount: unknown filesystem type 'users'

also is this how it suppose to look after the line was added

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c62656ec-4268-4baf-a6d1-8dd31f7bc52a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=3b89a995-53ff-4d8c-8f34-61abc60fc25e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=06ba37c5-4b9c-431e-9b5b-02bcd510d747 /media/Beta defaults,users 0 2   << this line

---

### Post by drs305 on 2009-01-17
> **-jay- said:**
> ok im getting to it but now get this
jay@jay-desktop:~$ sudo mount /dev/sda1
mount: unknown filesystem type 'users'

Well, we are making progress! I omitted the filetype. Copy/paste this entry into fstab.

Delete the previous line you entered into fstab and copy this line into fstab:
```

UUID=06ba37c5-4b9c-431e-9b5b-02bcd510d747 /media/Beta ext3 defaults,users 0 2

```
Save the file and then run the unmount/mount commands again.

---

### Post by -jay- on 2009-01-17
thank you very much problem solved i rebooted 2 times & it was still mounted again thank you

---

### Post by -jay- on 2009-01-21
ok im having a problem now when i reboot the partition i have mounted does not show up on desktop anymore how do i ad the icon back thanks

---

### Post by buzz57 on 2009-01-21
looks like you have missed out the filetype ext3 in your fstab file. look at earlier post

---

### Post by dphirschler on 2009-02-24
> **-jay- said:**
> ok im having a problem now when i reboot the partition i have mounted does not show up on desktop anymore how do i ad the icon back thanks

A long shot here, but did you by chance move the mount point to /mnt instead of /media?  I only ask because I recently discovered that mounts in /mnt do not show up on the desktop nor under 'Places', but mounts under /media do.  Since I am a noob too, that is all I have to offer.  Hope it helps.


Darryl

---

### Post by Slim Odds on 2009-02-24
/media is where Ubuntu puts drives that are mounted dynamically (i.e., when you plug them in).

You really should not mount permanent stuff there.

If you want an icon, just make a link to the drive (on your Desktop).

---

