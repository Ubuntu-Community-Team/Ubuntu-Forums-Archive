---
title: "partitions lost  bad superblock??"
date: 2009-04-03
forum: General Help
---

### Post by wardy277 on 2009-04-03
Hi,

I have been running intepid fine since release. had no problems and everything has been great. Then a couple of times i have gone into standby and on resume it has got stuck on a black screen. tried ctrl + alt + bacspace and ctr + printscreen + i etc but that didnt work so i held the power button, once it booted fine, then the second time it tried to do a disk check during boot, but that gave some errors so i used the fsck which gave some superclock errors. on boot i got a grub error (didnt list os').

i went into a live cd that i have (jaunty beta) and it couldn't mount it. The drive is set-up with the first half in NTFS for vista and the second partition with ubuntu (ext3 and swap) then a vista recovery partition. i culd mount the vista partition fine but the linus partition had a bad superblock.

on mount i got:

```

# mount /dev/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

```

so i ran the dmesg | tail and got:
```

[  111.212686] mtrr: no MTRR for d0000000,10000000 found
[  119.984050] wlan0: no IPv6 routers present
[  548.000088] CE: hpet increasing min_delta_ns to 15000 nsec
[  608.945696] wlan0: authenticate with AP 00:90:4c:7e:00:6e
[  608.959699] wlan0: authenticate with AP 00:90:4c:7e:00:6e
[  608.961660] wlan0: authenticated
[  608.961668] wlan0: associate with AP 00:90:4c:7e:00:6e
[  608.964874] wlan0: RX ReassocResp from 00:90:4c:7e:00:6e (capab=0x401 status=0 aid=2)
[  608.964882] wlan0: associated
[ 1471.912181] VFS: Can't find ext3 filesystem on dev sda1.

```


I found some forums on using testdrive. so i did that, it found my drive and partitions. so i use the analyse, scan, then a deep scan, then write. I thought this would fix it all but after a reboot it seems to have killed all the partitions, now GParted shows it as all unallocated except for the vista recovery?

does anyone know how to fix this? What is a superblock that it mentioned?

Chris

---

### Post by wardy277 on 2009-04-03
i have managed to restore the partitions, but i still cant get the ext3 mounted. GParted says its unknown

Chris

---

