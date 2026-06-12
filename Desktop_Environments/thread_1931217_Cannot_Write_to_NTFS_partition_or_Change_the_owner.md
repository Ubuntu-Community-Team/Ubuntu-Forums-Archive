---
title: "Cannot Write to NTFS partition or Change the ownership from root"
date: 2012-02-25
forum: Desktop Environments
---

### Post by strider357 on 2012-02-25
Hi,
I have an NTFS partition(/dev/sda4) with the LABEL="New Volume" which i used to mount without any problem (i.e. i could read and write files to this partion as a normal user)  using the following line in the /etc/fstab file

```
/dev/sda4	/media/MyDisk	ntfs	noexec,rw	0	0
```

But recently i have changed the label of the NTFS partition(I dont know why, probably just for fun ](*,)) to "MaveriK". After that i have a problem accessing the NTFS volume as a normal user. I couldnt even view the partition. I thought maybe tweaking the /etc/fstab would solve the problem

```
/dev/sda4	/media/MyDisk	ntfs-3g	exec,rw,umask=000,users	0	0
```

After changing this i could only view the partion as a normal user, but still the ownership of the NTFS volume is only to root(even after using umask=000) and i can no longer modify the files on this partition.
Please suggest what i could possibly do to use the partition as a normal user.
Thanks in advance.

---

### Post by Morbius1 on 2012-02-25
It's possible that the partition is no longer sda4. That happens and it's why the current way to mount partitions is with UUID's not the legacy /sdxy designation. 

** Run the following command and see if it's mounted where you think it's mounted:
```
mount
```** Confirm how the system sees that partition:
```
sudo blkid -c /dev/null
```** Unmount the partition:
```
sudo umount /media/MyDisk
```And redo the line in fstab to something like this:
```
UUID=DA9056C19056A3B3 /media/MyDisk ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```[COLOR=Blue]*Change the DA9056C19056A3B3 part to the number you get from the "blkid" command.*[/COLOR]

Then run the following command to test for errors and if there are none mount the partition with the new fstab definition:
```
sudo mount -a
```

---

### Post by strider357 on 2012-02-25
Yes i have changed the mount option with the UUID of the ntfs partition in /etc/fstab as suggested. The partition mounts at startup without any errors. But still i can READ ONLY the files as a normal user. I am not able to write to that partition unless i use a root access.

---

### Post by Morbius1 on 2012-02-25
I wonder if the package ntfs-3g is not installed in which case it would be the old read only version.

Install it:
```
sudo apt-get install ntfs-3g
```
If it's already there reinstall it:
```
sudo apt-get --reinstall install ntfs-3g
```
You will have to unmount and then "sudo mount -a" again.

---

### Post by strider357 on 2012-02-25
Hi Morbius1, thanks for trying to help me out.
I have installed ntfs-3g also but it didnt do much help.

I actually installed Ubuntu 11.10 recently and i could mount the ntfs partion(LABEL="New Volume") as a normal user(without modifying /etc/fstab) and i also had R/W permissions. I think its a problem of ownership on the ntfs partition. I still have same version of Ubuntu but after changing the ntfs volume label recently, it is owned by ROOT and i am not able to mount or have R/W permissions on the ntfs partition as a NORMAL user.

---

### Post by p-dh on 2012-02-25
From my experience, changing the user or rights on an NTFS partition doesn't work easily (something that messes me up whenever I set up Unison to synchronize between my server and an NTFS drive). Anyhow, I have had no problems with mounting my drives - and accessing them by simply using the defaults option in fstab. My fstab entry looks like:

> UUID=72047E4A047E10F9 /media/lwdata ntfs-3g defaults 0 0

This applies for all of my NTFS partitions and allows for them to be properly handled if I boot into Windows.

Peace,
Paul :cool:

---

### Post by strider357 on 2012-02-25
Hi Paul as i had mentioned earlier the /etc/fstab entry worked fine to me(I had R/W permissions as normal user), but that was before i changed the ntfs volume name. Only after changing the ntfs volume name i am starting to have problems.

So could you please help me out with changing the user rights on the ntfs partition without messing with the data present there.

---

### Post by strider357 on 2012-02-26
I have been tweaking with /etc/fstab. Thankfully the following mount options in the /etc/fstab to mount my ntfs partition has given me R/W permissions as a normal user:
```
UUID=77777777779257C7	/media/MyDisk	ntfs-3g	exec,rw,umask=000,users,[COLOR="Blue"]gid=users[/COLOR] 0 0
```

Adding gid=users in the mount options has done the job. Now i can read and write to that ntfs partition.:grin:

Thanks for trying to help me out.

---

