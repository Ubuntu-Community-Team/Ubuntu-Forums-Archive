---
title: "Tool/way to increase root.disk -- gparted not possible"
date: 2009-06-16
forum: General Help
---

### Post by luisridaocruz on 2009-06-16
This question has been addressed in the forums before but I have so far not found a definitive
answer to my problem.
My root.disk is full and I want  to increase it.

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       **13G   13G   45M 100% /**
tmpfs                 989M     0  989M   0% /lib/init/rw
varrun                989M  124K  989M   1% /var/run
varlock               989M     0  989M   0% /var/lock
udev                  989M  172K  989M   1% /dev
tmpfs                 989M     0  989M   0% /dev/shm
/dev/sda1              61G   33G   28G  54% /host
lrm                   989M  2.7M  987M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             233G  165G   69G  71% /media/New Volume
/dev/sda2              89G   44G   46G  49% /media/Data

The GParted program won't allow me to do it as it is not possible on NTFS fyle sistem.
Another solution was if I remember well to insert an UBUNTU CD (last release) and resize from here
but I haven't found any manual on how to do it (I don't wish to initiate something that can cause more problems than I already have)

Thanks in advance

---

### Post by Cheesemill on 2009-06-16
Did you install using Wubi?
If so then I don't believe it's possible.

---

### Post by luisridaocruz on 2009-06-16
No, Wubi is not installed on my system.
I don't even know what Wubi is.

Thanks in advance

---

### Post by Legace on 2009-06-16
> **luisridaocruz said:**
> No, Wubi is not installed on my system.
I don't even know what Wubi is.

Thanks in advance

Did you install Ubuntu through Windows?

---

### Post by luisridaocruz on 2009-06-16
Yes I installed Ubuntu through Windows

---

### Post by Cheesemill on 2009-06-16
> **luisridaocruz said:**
> Yes I installed Ubuntu through Windows

That's what Wubi is (Windows UBuntu Installer) :)

---

### Post by luisridaocruz on 2009-06-16
Thanks for the tip but How can I then increase my root.disk to, lets say 20 GB from the current 13 GB?

Thanks in advance

---

### Post by sedawk on 2009-06-16
First, your root partition is not NTFS I think, but ext2 or ext3.
(Output of "mount"?)

It looks like you have your /home directory on the root partition.

So the easiest way to proceed is to create a partition for /home directory.
See the following instructions. (Use at your own risk. Make a backup of /home!)

1) Create a new partition for /home
2) Mount the new home to a temporary directory e.g.
   sudo mkdir /new_home
   sudo mount /dev/sdX/sdXN /new_home
3) copy data from old /home to new /new_home
   (e.g. "sudo rsync -av /home/ /new_home/")
   The slashes in the rsync are important!
4) Edit /etc/fstab to mount "/new_home/" to "/home" with next boot
   Check that /home and /new_home have the same content.
4.1) Now you can (if you want to) delete some big files from /home but
   do not fully remove it or the content - only do this if you know
   what you do (e.g. deleting video files, or big downloads, or ...
   you should have a backup of these files in /new_home already!)
5) Boot your system and check /home works 
   (This new partition mounted at /home hides your old /home directory
   still located on the root partition and wasting space.See next step)
6) Boot from a LiveCD and mount your root partition 
   (To a temporary directory like /mnt or /media/root, see above).
   Now the old /home directory is available at /mnt/home or
   /media/root/home so you can now delete the directory to
   free space on your root partition.

Alternatively you can move /home to another (existing) partition
and use a symbolic links that points from /home to the new
location of home. But that is not as good as the above solution.

It is always a good idea to put /home to a different partition because
than you can reinstall Linux on the root partition without loosing
your home data. (You can even install Ubuntu and Fedora in parallel
and use the same /home directory, although this might get you in
trouble when the configuration data in your home is not compatible
with both Linux versions).

---

### Post by Cheesemill on 2009-06-16
Again, as you installed Ubuntu through Windows, I don't think it's possible to increase the size of the install.

This is because Ubuntu isn't installed on it's own partition as it would have been with a normal install, it's installed on a virtual partition on your NTFS drive.

See here for more info:
[http://ubuntuforums.org/showthread.php?t=776592](http://ubuntuforums.org/showthread.php?t=776592)

---

### Post by LowSky on 2009-06-16
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

