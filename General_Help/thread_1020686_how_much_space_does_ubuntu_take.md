---
title: "how much space does ubuntu take?"
date: 2008-12-24
forum: General Help
---

### Post by stmartin on 2008-12-24
Hello!

I got ubuntu 8.04 Hardy Heron, and when I see in System Monitor, there are only 5GB free space out of 18GB. I got only installed some programs and Edubuntu.

/dev/sda6              19G   14G  3.8G  79% /
varrun               1014M  224K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   48K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-22-generic/volatile
/dev/sda1              31G   15G   16G  48% /media/windows
/dev/sda5             100G   67G   33G  68% /media/localdiscd

Regards.

---

### Post by taurus on 2008-12-24
Make sure you empty your trash bin because when you delete something with nautilus, you just only move it to trash bin.  As a result, it will take up the space on your harddrive.  

Also, look in /var to make sure you don't have some large directories like /var/backups.

```
sudo du -h /var/backups
sudo apt-get clean
df -h
```

---

### Post by leva on 2008-12-24
/dev/sda6 19G 14G 3.8G 79%

is that where you have it installed to?

---

### Post by stmartin on 2008-12-24
Yes, it is sda6.

Also I had one 7GB folder which I moved to trash, but when I tried to remove it said, Directory is not empty. So I deleted using terminal. 

@taurus I used your advises, but the backups folder was only 5.5 MB.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              19G   14G  4.1G  77% /
varrun               1014M  228K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   48K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-22-generic/volatile
/dev/sda1              31G   15G   16G  48% /media/windows
/dev/sda5             100G   67G   33G  68% /media/localdiscd
gvfs-fuse-daemon       19G   14G  4.1G  77% /home/stefan/.gvfs

---

### Post by stmartin on 2008-12-24
Yes, it is sda6.

Also I had one 7GB folder which I moved to trash, but when I tried to remove it said, Directory is not empty. So I deleted using terminal. 

@taurus I used your advises, but the backups folder was only 5.5 MB.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              19G   14G  4.1G  77% /
varrun               1014M  228K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   48K 1014M   1% /dev
devshm               1014M   12K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-22-generic/volatile
/dev/sda1              31G   15G   16G  48% /media/windows
/dev/sda5             100G   67G   33G  68% /media/localdiscd
gvfs-fuse-daemon       19G   14G  4.1G  77% /home/stefan/.gvfs

---

### Post by stmartin on 2008-12-25
BUMP! Help please!

---

### Post by kaibob on 2008-12-25
You can run the following command in a terminal window to see if any really large files show up. This command finds any files in excess of 10 mb.

```
sudo find / -xdev -size +10M -type f -exec ls -gohX {} \;
```

You may also want to open synaptic and select *settings > preferences > files* and click on "Delete Cached Package Files."

---

### Post by stmartin on 2008-12-26
Thanks for the post. It helped. I sow that in the Trash folder of the root user there was the output folder (a back up folder around 10GB), which I deleted using command line of my basic user (because it would not delete from Trash). It seemed like it was deleted. But now I found it. How is that possible?

Regards.

---

### Post by kaibob on 2008-12-26
> **stmartin said:**
> Thanks for the post. It helped. I sow that in the Trash folder of the root user there was the output folder (a back up folder around 10GB), which I deleted using command line of my basic user (because it would not delete from Trash). It seemed like it was deleted. But now I found it. How is that possible?

Regards.

This could happen if you started nautilus with gksudo. I didn't think files went to the trash if deleted from the terminal, so I'm not sure about this.

---

### Post by noletolucas on 2010-10-29
A FRESH Ubuntu 10.04 install takes up **2.1 gb**.

Just installed.

---

### Post by Verbeck on 2010-10-29
> **noletolucas said:**
> A FRESH Ubuntu 10.04 install takes up **2.1 gb**.

Just installed.
the thread is 2 years old and refers to  8.04

---

