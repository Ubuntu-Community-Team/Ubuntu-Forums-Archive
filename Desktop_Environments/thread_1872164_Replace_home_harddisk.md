---
title: "Replace /home harddisk"
date: 2011-10-30
forum: Desktop Environments
---

### Post by menixmatrix on 2011-10-30
I have a computer with 2 hard disks in it,one is with swap and os and second one is mounted /home.
I will like to replace the /home mounted hd with a bigger one (ex. 1000gb)
What is the best procedure to do this?
Except reinstalling the os ;)

---

### Post by Lars Noodén on 2011-10-30
Can you have three disks in the machine at the same time?  If so then the solution is to put in the third disk mount it somewhere and then use tar or rsync to copy the files (and links) over.  

Otherwise, you'll have to put the new disk in and restore to it from your external backup.

---

### Post by menixmatrix on 2011-10-30
Using rsync or tar will make the new hd became /home as well? If I want to restore it from the backup, when I login again then he will create a new profile in the /home directory in the first hd and I can not mount any hd to a populated directory? Do I need to log in in the terminal or remote ssh and mount the new hd in the fstab? then restore the backup, then login normally?

---

### Post by Theredbaron1834 on 2011-10-30
nevermind.. Sorry.

---

### Post by paulisdead on 2011-10-30
Format the drive as ext4 or whatever you want.  Mount the drive up somewhere, like /mnt/home.  Whatever method you use to copy the files over, you need to make sure it preserves permissions.  Simple "cp -Rp" will do that, or "rsync -avrt" as well.  Once your stuff is copied, run "blkid" from the CLI, to find out the UUID of the partition you made on the new drive.  Edit your /etc/fstab file to reflect the UUID of the new drive on the line for /home, reboot and it should now be mounted up as /home.

---

