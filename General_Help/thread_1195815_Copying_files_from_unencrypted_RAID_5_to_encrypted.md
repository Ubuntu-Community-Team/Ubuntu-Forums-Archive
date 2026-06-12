---
title: "Copying files from unencrypted RAID 5 to encrypted RAID 5 results in crash"
date: 2009-06-24
forum: General Help
---

### Post by ricmitch on 2009-06-24
Running Jaunty server.

I have two RAID 5 arrays, both reiserfs, one encrypted using luks one unencrypted. I want to copy all files from the unencrypted array to the encrypted one. Whenever I copy files, perhaps 50 are copied across before the system crashes and restarts. There are no clues in /var/log/messages. Just before the crash kcryptd is using about 60% CPU.

The command I use to copy files is:
cp --no-dereference -R -v /mnt/old-media/* /var/media/

The crash does not occur when copying the same file each time. reiserfsck reports no problems.

Anyone got any ideas at least how I can get more information on what's going wrong?

---

### Post by ricmitch on 2009-06-24
Follow-up:
```
~$ uname -a
Linux chronos 2.6.28-13-server #44-Ubuntu SMP Tue Jun 2 08:40:28 UTC 2009 x86_64 GNU/Linux

```

```

~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdd1[1] sde1[2] sda1[0]
      1953519872 blocks level 5, 128k chunk, algorithm 2 [3/3] [UUU]
      
md0 : active raid5 sdb1[2] sdc1[0]
      976767744 blocks level 5, 128k chunk, algorithm 2 [3/2] [U_U]
      
unused devices: <none>

```

```

~# cryptsetup status md1encrypted
/dev/mapper/md1encrypted is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/md1
  offset:  2056 sectors
  size:    3907037688 sectors
  mode:    read/write

```

---

### Post by ricmitch on 2009-06-25
Top at the time of the crash & reboot.

(Just to confuse you, I've switched around md0 and md1 now.)

---

### Post by ricmitch on 2009-06-26
bump!

---

### Post by ricmitch on 2009-06-26
The issue is definitely caused by the encryption. I formatted the array with Reiser without encryption and writing files is fine.

---

### Post by ricmitch on 2009-06-27
OK it wasn't just the encryption, it's some combination of RAID and high CPU usage. The same reboot occurs when copying large files from an NTFS volume to the unencrypted RAID array.

---

### Post by ricmitch on 2009-06-27
smartctl and memtest86+ report no problems.

kdump does not catch a vmcore dump - at the end of my tether now :(

---

### Post by ricmitch on 2009-06-27
Adding:
```
apm=off acpi=off ide=nodma nopcmcia noapm noacpi nofb
```
To the kernel line in menu.lst seems to have helped (touch wood), though still doesn't really explain why the reboots were happening in the first place.

---

### Post by Per Olav on 2009-06-27
I've been using encrypted sw raid5 for a long time, and I have never seen it crash bacause of high load. It's normal for the kcryptd to use a lot of CPU when there's heavy I/O on the array. 
I've tried out luks-raid-lvm, raid-lvm-luks, and raid-luks-lvm combinations.
(sticked with raid-luks-lvm)

The only time I have had a array crash, was a disk with a mechanical fault, which really disappointed me, because it beats the whole idea of using raid in the first place. That incident moved me over to hardware raid (3Ware)

I see that one of your arrays are degraded, is this intentional?, ie. during some migration from a set of drives to another?

---

### Post by ricmitch on 2009-06-27
Yes, I'm migrating from an old, degraded array to a new one.

---

