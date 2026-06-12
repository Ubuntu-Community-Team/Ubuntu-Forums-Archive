---
title: "Can't create directory"
date: 2009-04-13
forum: General Help
---

### Post by Jongi on 2009-04-13
Am I missing something here? I want the normal user jongi to be able to have write access to /data

```

root@xububtu-desktop:~# cat /etc/fstab | grep data
# /data was on /dev/sda8 during installation
UUID=b555bd06-30f1-4f1d-a739-c4bfac62d4f4 /data           ext4    relatime,user,rw        0       2
root@xububtu-desktop:~# umount /data/
root@xububtu-desktop:~# mount -a
root@xububtu-desktop:~# exit
logout
jongi@xububtu-desktop:~$ mkdir /data/profile
mkdir: cannot create directory `/data/profile': Permission denied

```

---

### Post by taurus on 2009-04-13
Why not just modify the entry for /dev/sda8 to make it look like this in /etc/fstab?

```
UUID=b555bd06-30f1-4f1d-a739-c4bfac62d4f4 /data           ext4    relatime        0       2
```
Then, change the ownership of /data from root to your login name so you can write to it anytime you want.

```
sudo chown -R jongi:jongi /data
mkdir /data/profile
ls -la /data
```

---

### Post by Jongi on 2009-04-13
i intend on having a numer of distros installed that will write to that partition. i like to think that fstab can set it such that i can state any user can write to a partition.

the course of making sure that every user in each distro has the same UUID creates a lot of work.

---

### Post by taurus on 2009-04-13
```
sudo chmod 777 /data
mkdir /data/profile
```

---

