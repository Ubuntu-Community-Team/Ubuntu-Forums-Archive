---
title: "auto mount all hard disks without editing /etc/fstab ?"
date: 2009-06-12
forum: General Help
---

### Post by uarale on 2009-06-12
On fedora 10 i found that all the partitions are mounted after start-up without any click or command. Also noted that in /etc/fstab there are only 2 mount points for / and swap.

The question is: how to do it on ubuntu (of course when leaving /etc/fstab alone)?

---

### Post by kerry_s on 2009-06-13
> **uarale said:**
> On fedora 10 i found that all the partitions are mounted after start-up without any click or command. Also noted that in /etc/fstab there are only 2 mount points for / and swap.

The question is: how to do it on ubuntu (of course when leaving /etc/fstab alone)?

are you sure there mounted or just detected?
it's usually not mounted till you click on it, if it is auto mounted that would put things at risk, a power outage or crash could take them out with the rest of the system.

---

### Post by dcstar on 2009-06-13
> **uarale said:**
> On fedora 10 i found that all the partitions are mounted after start-up without any click or command. Also noted that in /etc/fstab there are only 2 mount points for / and swap.

The question is: how to do it on ubuntu (of course when leaving /etc/fstab alone)?

Install the pysdm package and use it to set up the fstab entries.

---

### Post by uarale on 2009-06-14
> **kerry_s said:**
> are you sure there mounted or just detected?
it's usually not mounted till you click on it, if it is auto mounted that would put things at risk, a power outage or crash could take them out with the rest of the system.

i am certain that all internal partitions and eternal disks are MOUNTED (with an up-arrow in nautilus).

and as i stated, there are only 2 mount points in /etc/fstab

---

### Post by elhigu on 2011-05-06
I got tired to look for answer to this question, people says that install hal/dbus but I didn't got a lot success with them with my live cd project. Anyways I found it easier to just use half an hour to write script, which work perfectly for my use. 

Dummy script checks all found disk uuids and creates new mount point for each partition and tries to mount disk to corresponding directory.  All disks will be mounted under /automount directory.

Maybe suitable place to put this script would be /etc/rc5.d, I have stored script in /root/automount.sh and made symlink 

```
ln -s /root/automount.sh /etc/rc5.d/S80automount-all-drives
```

Script tries to mount first without any specific partition type. If mounting fails, then it tries mount as ntfs and if it fails it tries to mount partition as fat32.

Script also chekcs, if mount point is already used, so it wont fail really ugly if it is run multiple times. You can run the script directly from command line as well and it needs root privileges.

ps. If someone has detailed info how to do this easier, please share! I would have preferred just to do apt-get install something, which magically makes all partitions to be mounted somewhere when livecd boots.

------------ automount.sh ------------

```
#/bin/sh

disks=$(ls -1 /dev/disk/by-uuid)

for uuid in $disks;do
    disk=/dev/disk/by-uuid/$uuid
    mount_point=/automount/$uuid
    
    if ! grep $mount_point /proc/mounts;then

	mkdir -p $mount_point
	chmod gou+rwx /automount
	chmod gou+rwx $mount_point 

	fail=''
	if ! mount $disk $mount_point;then
	    if ! mount -t ntfs $disk $mount_point;then
		if ! mount -t vfat $disk $mount_point;then
		    echo "Failed mounting with -t ntfs -t vfat and without -t"
		    echo "Could not mount $disk check type and fix the script"
		    fail="could not mount"
		fi
	    fi
	fi 
	
	if [ -z $fail ];then
	    echo "Mounted $disk to $mount_point"
	else
	    echo "Could not mount $disk, check if partition is ok or if script should be fixed" 
	fi
    else
	echo "$mount_point is already mounted" 
    fi
done
```

---

