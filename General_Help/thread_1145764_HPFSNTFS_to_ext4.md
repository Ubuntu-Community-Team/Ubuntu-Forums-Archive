---
title: "HPFS/NTFS to ext4"
date: 2009-05-01
forum: General Help
---

### Post by burakvarhan on 2009-05-01
Hello,

I have a partition /dev/sda7 that I formatted to NTFS before. Now I want to format it with ext4 filesystem. However, despite I tried the command "mkfs -t ext4 /dev/sda7" and it seemed to worked, the output of "fdisk -l" still shows that /dev/sda7's filesystem is  HPFS/NTFS.

I am using Ubuntu 9.04. Below is the output of "fdisk -l". Could someone please tell me how can I format that drive to ext4?

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864       14593    78156225    5  Extended
/dev/sda5            4864        6079     9767488+  83  Linux
/dev/sda6            6080        9726    29294496   83  Linux
/dev/sda7            9727       14224    36127744    7  HPFS/NTFS
/dev/sda8           14225       14593     2963961   82  Linux swap / Solaris

Thank you.

---

### Post by mkoehler on 2009-05-01
It's easiest if you just use the partition editor on the live cd.  In order to format a disk, it has to be unmounted - Just delete the /dev/sda7 partition using the graphical editor and create a new partition (ext4).

---

### Post by jbrown96 on 2009-05-01
That command should work. I'm not sure why your still seeing it as NTFS. Using gparted, as the previous poster suggested, is a fairly fail-safe method. However, the linux nerd in me doesn't like being forced to use a GUI app! have you tried mounting the partition with ```
sudo mount -t ext4 /dev/sda7 /MOUNT/FOLDER
``` where /mount/folder is an empty folder?


you could also try overwriting the partition with either ```
sudo shred -n 0 -zvv /dev/sda7
``` or ```
sudo dd if=/dev/zero of=/dev/sda7
``` You don't need to let these commands run for long. They will destroy the partition in a matter of seconds. Use Ctrl+c to stop the commands. Then run your mkfs command from earlier. What does fdisk -l report?

---

### Post by burakvarhan on 2009-05-04
Thank you very much jbrown96 and mkoehler,

I took the Live CD approach and after deleting and re-creating the partition, format to ext4 worked.

---

