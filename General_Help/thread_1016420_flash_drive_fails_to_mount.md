---
title: "flash drive fails to mount"
date: 2008-12-19
forum: General Help
---

### Post by 2handband on 2008-12-19
Here's an odd problem: my Intrepid installation has suddenly stopped recognizing my USB flash drive. The weird thing is that I'm running XP Pro on a virtual machine over the top of Intrepid on that's reading the flash drive just fine. The Intrepid install on my wife's computer also reads it no sweat. Does anyone know what might be causing this?

---

### Post by taurus on 2008-12-19
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by 2handband on 2008-12-19
"ene@gene-laptop:~$ sudo fdisk -l
[sudo] password for gene: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x87c675e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648       23099   156248190   83  Linux
gene@gene-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              28G  8.3G   18G  32% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  304K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  2.8M  1.9G   1% /dev
tmpfs                 1.9G  204K  1.9G   1% /dev/shm
lrm                   1.9G  2.4M  1.9G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda2             148G  1.1G  140G   1% /media/Data"

I should also point out that my other flash drive mounts just fine.

---

