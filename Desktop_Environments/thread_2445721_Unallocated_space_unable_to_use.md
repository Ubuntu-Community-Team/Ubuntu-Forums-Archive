---
title: "Unallocated space unable to use"
date: 2020-06-18
forum: Desktop Environments
---

### Post by ringworm24 on 2020-06-18
Totally new to this, but I have installed ubuntu 20 and have noticed my drive is tiny (46.62gb).. I have freed up space. But I can not add the unallocated space to my personal drive . How do I do this?

---

### Post by #&amp;thj^% on 2020-06-18
Gparted is a good tool for that>>[https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions](https://gparted.org/display-doc.php%3Fname%3Dmoving-space-between-partitions)
Just a heads up>>> You won't be able to resize any partitions that are actively in use
Also would be helpful to see this from the terminal.
```
df -H
```

---

### Post by ringworm24 on 2020-06-18
My drive is actively in use, so what are the options now?

---

### Post by #&amp;thj^% on 2020-06-18
Boot from a Gparted usb/cd/dvd.
Even boot from your installer for ubuntu, the run gparted from there. [https://gparted.org/liveusb.php](https://gparted.org/liveusb.php)
Still have not seen your return from:
```
df -H
```
I would like to see that before you proceed with gparted suggestion.

---

### Post by ringworm24 on 2020-06-18
[HTML]Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  2.1M  1.6G   1% /run
/dev/sdb4        46G   38G  6.2G  86% /
tmpfs           7.8G  376M  7.5G   5% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop0      107M  107M     0 100% /snap/burdirc/1
/dev/loop3      141M  141M     0 100% /snap/gnome-3-26-1604/98
/dev/loop1       98M   98M     0 100% /snap/core/9289
/dev/loop4      162M  162M     0 100% /snap/gnome-3-28-1804/128
/dev/loop5      157M  157M     0 100% /snap/gnome-3-28-1804/110
/dev/loop2      141M  141M     0 100% /snap/gnome-3-26-1604/100
/dev/loop8      2.5M  2.5M     0 100% /snap/gnome-calculator/748
/dev/loop6       55M   55M     0 100% /snap/core18/1279
/dev/loop7      256M  256M     0 100% /snap/gnome-3-34-1804/36
/dev/loop9      4.3M  4.3M     0 100% /snap/gnome-calculator/544
/dev/loop10     3.8M  3.8M     0 100% /snap/gnome-system-monitor/111
/dev/loop11      74M   74M     0 100% /snap/irccloud-desktop/101
/dev/loop12     2.3M  2.3M     0 100% /snap/gnome-system-monitor/148
/dev/loop14     164M  164M     0 100% /snap/spotify/41
/dev/loop13     182M  182M     0 100% /snap/spotify/36
/dev/loop15     145M  145M     0 100% /snap/notepadqq/855
/dev/loop16      55M   55M     0 100% /snap/core18/1754
/dev/loop18      63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop17      90M   90M     0 100% /snap/core/8213
/dev/loop19     1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop20      99M   99M     0 100% /snap/irccloud-desktop/113
/dev/loop21      45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop22     1.0M  1.0M     0 100% /snap/gnome-logs/100
/dev/loop23     384K  384K     0 100% /snap/gnome-characters/550
/dev/loop24      15M   15M     0 100% /snap/gnome-characters/367
tmpfs           1.6G   20K  1.6G   1% /run/user/121
tmpfs           1.6G   64K  1.6G   1% /run/user/1000
/dev/sda2       465G  460G  5.1G  99% /media/edward/01D122B65EEB0D70
[/HTML]

---

### Post by #&amp;thj^% on 2020-06-18
Ok Thanks.
Go ahead now with the Gparted route.
Good luck. ;)

---

### Post by grahammechanical on 2020-06-18
Excuse me, but where is this unallocated space? If it is in a partition then you need to shrink that partition and expand another partition to include the unallocated space. You may need to move other partitions in order to bring the unallocated space up to a boundary of the partition you want it to be in.

If the unallocated space is simply space on a drive that is not in a partition and it is up against the boundary of the partition that you want the unallocated space to be in, then you need to expand the partition to take up some or all of the unallocated space.

Before for you do any of this backup anything that you do not want to lose. If you do things correctly it is likely that no data will be lost. I have created; deleted and move partitions and not lost any data. But if I make a mistake in the instructions that I am giving Gparted, then I do not expect to get out of it without loss. Gparted will accept the instructions but not make any changes until you tell it to apply the changes.

When you run Gparted from a live session of Ubuntu it will give a representation of the partitions on the drives. Take a screen shot and post it here. Please.

Regards.

---

