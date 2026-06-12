---
title: "Strange partitions.."
date: 2007-04-06
forum: Desktop Environments
---

### Post by attorianzo on 2007-04-06
[center]
[[img]http://img381.imageshack.us/img381/7826/schermatafx1.th.jpg[/img] ](http://img381.imageshack.us/img381/7826/schermatafx1.jpg) [[img]http://img400.imageshack.us/img400/481/schermata1ru3.th.jpg[/img]](http://img400.imageshack.us/img400/481/schermata1ru3.jpg)
[/center]

In the first pic on the left there's the window that shows the output of "df" command, on the right, in the same pic, there is the "baobab analizer".

In the second pic there is what gparted shows of my hda unit.

hda1 is my first HD, 20Gb (800Mb swap, as you can see in the gparted pic)

What I'm not understanding is  that baobab says that root ("/") is only 9.5 Gb, but "df" command says that hda1 is 17 Gigas and only 800 Mb are free.

Here's the output of **df -h** :
```
$ df -h
Filesystem            Dimens. Usati Disp. Uso% Montato su
/dev/hda1             18G 17G 860M 96% /
varrun                252M 92K 252M 1% /var/run
varlock             252M     0 252M 0% /var/lock
procbususb             10M 140K 9,9M 2% /proc/bus/usb
udev                 10M 140K 9,9M 2% /dev
devshm                252M     0 252M 0% /dev/shm
lrm                 252M 17M 236M 7% /lib/modules/2.6.17-11-generic/volatile
/dev/hdc5             51G 29G 22G 58% /media/hdc5
/dev/hdc1             9,8G 6,6G 3,3G 68% /media/hdc1
/dev/hdc6             17G 2,9G 13G 19% /media/hdc6

```

Here's **fdisk -l** :

```
$ sudo fdisk -l
Password:

Disk /dev/hda: 20.4 GB, 20496236544 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot     Start         End     Blocks Id System
/dev/hda1 *         1        2386    19165513+ 83 Linux
/dev/hda2            2387        2491     843412+ 5 Esteso
/dev/hda5            2387        2491     843381 82 Linux swap / Solaris

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot     Start         End     Blocks Id System
/dev/hdc1 *         1        1275    10241406    7 HPFS/NTFS
/dev/hdc2            1276        9963    69786360    f W95 Ext'd (LBA)
/dev/hdc5            1276        7812    52508421    7 HPFS/NTFS
/dev/hdc6            7813        9963    17277876 83 Linux

```

---

