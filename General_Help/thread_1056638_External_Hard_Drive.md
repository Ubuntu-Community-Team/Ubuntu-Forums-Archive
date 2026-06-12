---
title: "External Hard Drive"
date: 2009-01-31
forum: General Help
---

### Post by dominiclajs on 2009-01-31
Hi,
I recently purchased a Moser Baer External Hard Drive (160 GB) HD160K200, I have Ubuntu 8.04 installed in my PC. When I connect the External Hard Drive to my PC I see "USB Drive" under computer:///. I am not able to mount the "USB Drive". Can anyone please say me what is the issue and what I need to do to access my external hard drive.

Regards,
Dominic L A J S

---

### Post by taurus on 2009-01-31
While the drive is still plugged, post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by dominiclajs on 2009-02-01
The output in my terminal is shown below:
I don't find my drive details here.

 sudo fdisk -l
[sudo] password for dominic: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0eb02c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris
dominic@dominic-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   27G  7.4G  79% /
varrun                629M  100K  629M   1% /var/run
varlock               629M     0  629M   0% /var/lock
udev                  629M   48K  629M   1% /dev
devshm                629M   12K  629M   1% /dev/shm
lrm                   629M   39M  590M   7% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       36G   27G  7.4G  79% /home/dominic/.gvfs

====================================================================================
Even if I go to partition editor I am not able to view this external hard disk.
Can you say me what i have to do to access it. It is a fresh new drive and I have no data in it.

---

### Post by taurus on 2009-02-01
Make sure it's plugged in and on, then post the output of this command.

```
dmesg | tail
```

---

### Post by suraponsivamok on 2009-02-05
I've got the same problem. Before upgrading to 8.10 from 8.04, just yesterday, my HFS+ hard drive normally appeared on the desktop and mount point /media/{the_volume_name}, which I used most of the time. I disconnected it before hitting "upgrade" in the update manager. After an overnight-long upgrade, I plugged it back again, nothing appears, no mount point, no /dev/sdb* at all. I plugged the problem external hard drive back to my macBook, it showed up and functional properly, but it didn't appear in Ubuntu on my another HP laptop.  Following are additional information.

>>> sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed56ed56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

>>> lsusb
Bus 004 Device 006: ID 059b:0178 Iomega Corp. Hi-Speed USB-to-IDE Bridge Controller
Bus 004 Device 003: ID 054c:031d Sony Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 045e:00a4 Microsoft Corp. 
Bus 001 Device 003: ID 03eb:0902 Atmel Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

>>> dmesg | tail
[ 1634.680343] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1634.680348] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1634.681478] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1634.681484] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1634.682603] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1634.682609] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1634.683733] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1634.683738] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1634.685751] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
[ 1634.685758] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information

***
Please help. I'm looking forward to your advice, thank you very much in advance.

---

### Post by suraponsivamok on 2009-02-05
I found another thread discussing this problem.
[http://forum.ubuntu-fr.org/viewtopic.php?pid=2301011](http://forum.ubuntu-fr.org/viewtopic.php?pid=2301011)
Would it be a remedy? (Sorry that it's in French, I can't find the relevant thread in English.) I will try it out after dinner.

---

### Post by suraponsivamok on 2009-02-05
I followed the instruction as in the thread above and it works. The HFS+ external hard drive comes back alive.

As said in the following link mentioned in the thread,
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983/comments/7](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983/comments/7)
I replace Intrepid 60-persistent-storage.rules with 65-persistent-storage.rules, restarted Ubuntu, in a few seconds, the drive appears on the desktop as it used to be.

---

### Post by Z3r0t0l0rEnCe on 2009-02-05
I had this problem once before.  Was it connected to Windows first? Because safely remove hardware would need to be done on Windows.  That happened to me when I connected via my XP. That my be your problem.

---

