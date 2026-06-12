---
title: "completely removing gnome and budgie from ubuntu 16.10"
date: 2017-01-26
forum: Desktop Environments
---

### Post by thedoctor818772 on 2017-01-26
Good Morning,

I currently have (I believe) Gnome and Bugdie DE both installed on top of my Ubuntu 16.10 machine and I do believe it is slowing down my machines performance. I tried to remove the gnome desktop with help from this link:

[http://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16]("http://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16")

and similar help (but forgot the webpage) for the budgie DE, but when I go to log-in, I still see all 3 options (actually 4: Ubuntu, GNOME, Budgie, and Unity 8). 

How can I completely purge Gnome and Budgie from my system?

Thanks,

-MD

---

### Post by vanadium on 2017-01-26
Difficult as such. What I do when I try out another desktop on my system, is take note of all packages that are going to be installed when the desktop is installed. Then you can later largely revert what has been done by explicitly removing these packages again. Then it may help to remove the default desktop package, ubuntu-desktop, if it is still there, and install it again: this will make sure that all default packages are in place.

Probably, a fresh reinstall is your quickest and best bet. You can do a reinstall without reformatting the drive. This will refresh the system files, but preserve your user data and config files. After installation, you only need to add applications that you did install yourself - their user configuration will have been preserved. Still, you should update your backup before doing this, because thee is always a risk that things go wrong.

---

### Post by ajgreeny on 2017-01-26
If you added those DEs recently and can remember more or less when it was, you may be able to find the (long) lists of packages that were added at the same time by checking log files.

Try parsing the dpkg logs with command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list all packages installed in date order.
That may at least give you some clues if you search for the terms **budgie** and **gnome-shell** in the list, and you can then, assuming you did not install other packages in the same activity, remove all packages that were installed at the same date and time.

Be careful not to remove anything that is installed that you know you need, and if you choose to add another DE in future it is worth keeping a copy of the terminal output showing all the extra packages that were installed at the same time.

---

### Post by thedoctor818772 on 2017-01-26
Please forgive my ignorance, but how do I accomplish a fresh reinstall?

Thanks.

---

### Post by ajgreeny on 2017-01-26
> **thedoctor818772 said:**
> Please forgive my ignorance, but how do I accomplish a fresh reinstall?

Thanks.
First backup all important personal files.
It would help to know what partitions you have at present before we tell you what is the best way to go from there, so please show us the output of terminal command ```
sudo parted -l
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

Have you tried my suggested command from post #3?
Did it not help at all, as I think it is a bit soon to consider reinstalling.

---

### Post by thedoctor818772 on 2017-01-26
It only goes back to 12/06/16 and I'm pretty certain I did the install of budgie and gnome DE way before that. Here is the contents of sudo parted -l: 

**```
**
Model: ATA ST500LT012-1DG14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number Start End Size Type File system Flags
1 1049kB 30.7GB 30.7GB primary ext4 boot
3 30.7GB 410GB 379GB primary ext4
2 410GB 500GB 90.1GB extended
6 410GB 491GB 80.9GB logical ext4
5 491GB 500GB 9215MB logical linux-swap(v1)
**
```**

---

### Post by thedoctor818772 on 2017-01-26
And of course I do not want to have to make a fresh reinstall either. Not sure what to do.

---

### Post by ajgreeny on 2017-01-26
OK. If you are not keen on reinstalling it may be simplest to just try to remove any obvious duplicate application types.
For example you may have more than one terminal-emulator, file-manager and text-editor which you can clean up, leaving the one you prefer. 
You can find the applications that are related to those types using the dash in Ubuntu and typing **text-editor**. It will show all installed applications that can be used to edit text.
Synaptic package manager is also a very good way of searching for packages, but you will have to install it as it is no longer a default in installations.

If you end up needing to reinstall we need to know which partition is which, and why you have extra partitions; I presume you perhaps have a separate /home partition.

One by one, can you now show us the output of these three commands
```
mount
```
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

### Post by vanadium on 2017-01-29
If you do not want to reinstall, then you should not if your system otherwise is in a good state. As you learned, a real "full uninstall" requires one to know all packages that have been added. If you do not have the list, and do not want to reinstall, then indeed just uninstall extraneous applications. It would also be safe to uninstall all gnome-shell packages to remove gnome-shell specific packages. You can see, add and remove packages in synaptic, as ajgreeny pointed out. You can install synaptic using software center (I assume) or with the command:
```

sudo apt install synaptic

```
For budgie you could do something similar. Search for "budgie" in synaptic. Probably, you also want to remove "tracker" which comes with budgie desktop (and sometimes has your CPU blow at 400%).

After that, you will be able to remove other packages that are no longer needed with the command (I do not know how to do this in synaptic) (*close* synaptic first before running the following command)
```

sudo apt autoremove

``` 

Once finished uninstalling packages and apps that you think are extraneous, I recommend to remove and reinstall ubuntu-desktop, a small meta-package. This will assure that everything of the default Ubuntu desktop is pulled back in in case you did remove something too much:
```

sudo apt remove ubuntu-desktop
sudo apt install ubuntu-desktop

```  

Finally, clean up once more:
```

sudo apt autoremove
sudo apt clean
sudo apt autoclean

```

---

### Post by thedoctor818772 on 2017-01-30
Sorry this took so long. Family things came up. Anyway here are the results of those commands:

```

mount
```

```

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2974132k,nr_inodes=743533,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=599176k,mode=755)
/dev/sda6 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=33,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=8983)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
/var/lib/snapd/snaps/ubuntu-core_423.snap on /snap/ubuntu-core/423 type squashfs (ro,relatime)
/var/lib/snapd/snaps/gallery-app_6.snap on /snap/gallery-app/6 type squashfs (ro,relatime)
/var/lib/snapd/snaps/address-book-app_11.snap on /snap/address-book-app/11 type squashfs (ro,relatime)
/var/lib/snapd/snaps/ubuntu-calendar-app_7.snap on /snap/ubuntu-calendar-app/7 type squashfs (ro,relatime)
/var/lib/snapd/snaps/camera-app_4.snap on /snap/camera-app/4 type squashfs (ro,relatime)
/var/lib/snapd/snaps/ubuntu-core_1357.snap on /snap/ubuntu-core/1357 type squashfs (ro,relatime)
/dev/sda3 on /home type ext4 (rw,relatime,data=ordered)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=599172k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/var/lib/snapd/snaps/ubuntu-core_1411.snap on /snap/ubuntu-core/1411 type squashfs (ro,relatime)
/dev/sdb1 on /media/thedoctor818/E275-5501 type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```

```

sudo blkid -c /dev/null


```

```

/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/sda1: UUID="139f4372-4b78-40c2-bf37-edb0db73c0a1" TYPE="ext4" PARTUUID="c542501e-01"
/dev/sda3: UUID="8c685fc7-0f56-4143-a2f9-eb10347126d1" TYPE="ext4" PARTUUID="c542501e-03"
/dev/sda5: UUID="9420db5b-bb1a-4c31-812d-84b19aa7f0ce" TYPE="swap" PARTUUID="c542501e-05"
/dev/sda6: UUID="bcad21ba-1356-4494-a53d-68eed2b6e710" TYPE="ext4" PARTUUID="c542501e-06"

```

```

cat /etc/fstab

```

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=bcad21ba-1356-4494-a53d-68eed2b6e710 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9420db5b-bb1a-4c31-812d-84b19aa7f0ce none            swap    sw              0       0
# home partition was added post-installation, by hand
UUID=8c685fc7-0f56-4143-a2f9-eb10347126d1    /home    ext4    defaults    0    2
/dev/disk/by-uuid/b2438bd2-3366-482b-a25d-db11de829362 /mnt/b2438bd2-3366-482b-a25d-db11de829362 auto nosuid,nodev,nofail,noauto 0 0

```

Thanks for the help!

---

### Post by thedoctor818772 on 2017-01-30
So, how would I go about reinstalling then? Or is that now not my best option?

Thanks.

-MD

---

