---
title: "tmpfs, varlock, rootfs 100% full"
date: 2009-06-04
forum: General Help
---

### Post by narcoleptik.ninja on 2009-06-04
I have a 52G partition which is a sole USB drive that my ubuntu server runs on. It says it is at 100% and I do not know how it accumulated so much so quickly. I removed zoneminder which I think it like 4 gigs (I might be wrong), but it still says it is 100%. Also, I cannot remove some packages, it gives the followinge error: 

```

After this operation, 62.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 103137 files and directories currently installed.)
Removing evolution-common ...
Removing evolution-documentation-en ...
Removing evolution-webcal ...
Removing gnome-pilot-conduits ...
Removing gnome-pilot ...
Removing gnome-system-tools ...
Removing libdmx1 ...
Removing libexchange-storage1.2-3 ...
Removing libgnome-pilot2 ...
Removing libgtkhtml-editor0 ...
Removing libgtkhtml-editor-common ...
Removing libgtkhtml3.14-19 ...
Removing liblpint-bonobo0 ...
Removing libpisync1 ...
Removing libpisock9 ...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/10346: No space left on device
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```Here is my df -h

```
~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                  53G   52G     0 100% /lib/init/rw
varrun                1.9G  320K  1.9G   1% /var/run
varlock                53G   52G     0 100% /var/lock
udev                  1.9G  164K  1.9G   1% /dev
tmpfs                 1.9G  164K  1.9G   1% /dev/shm
rootfs                 53G   52G     0 100% /
/dev/sdd1             932G  910G   22G  98% /mnt/mainbackup1tb
/dev/sdc1             150G  121G   29G  81% /mnt/venus160gb
/dev/sda1             932G  896G   36G  97% /mnt/mainstorage1tb

```

---

### Post by blueridgedog on 2009-06-04
What is the output of 

```
cd /
sudo du --max-depth=1 | sort -g
```


and the output of 

```
sudo fsdisk -l
```

?

---

### Post by dcstar on 2009-06-05
> **narcoleptik.ninja said:**
> I have a 52G partition which is a sole USB drive that my ubuntu server runs on. It says it is at 100% and I do not know how it accumulated so much so quickly.
........
```
~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                  53G   52G     0 100% /lib/init/rw
varrun                1.9G  320K  1.9G   1% /var/run
varlock                53G   52G     0 100% /var/lock
udev                  1.9G  164K  1.9G   1% /dev
tmpfs                 1.9G  164K  1.9G   1% /dev/shm
**rootfs                 53G   52G     0 100% /**
/dev/sdd1             932G  910G   22G  98% /mnt/mainbackup1tb
/dev/sdc1             150G  121G   29G  81% /mnt/venus160gb
/dev/sda1             932G  896G   36G  97% /mnt/mainstorage1tb

```

Heaps of posts already about full root partitions, boot off a Live CD and clean out the log files as a start.

---

