---
title: "Trying to repartition"
date: 2009-04-25
forum: General Help
---

### Post by gibxam on 2009-04-25
Hey Ubuntuers,

I've been trying to repartition my hard drive and the last couple times haven't gone so well so I thought I would ask about it first this time. I already have Ubuntu installed and I used gparted to basically cut it in half and I'm trying to get another distrobution on the other half. Can I use both sda2/sda5 from the first my Ubuntu partition as a swap/Exetended partition for the new one that I am making? How would I do this? This is what my /dev/sda looks like with fdisk:
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4477        9324    38941560   83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda5            9325        9726     3229033+  82  Linux swap

```

I want to put the other distrobution from 1 to 4476. Thank you for any help.
Max

---

### Post by Seks on 2009-04-25
Just choose manual partitioning when you install, that way you can set sda5 to be used as the swap and can format the unused space at the beginning to put the system, everything else is automatic

---

### Post by gibxam on 2009-04-25
The distrobution doesn't have an installer ;) could I just use mke2fs and mkswap and swapon on for the already swap partitions?

---

### Post by ibuclaw on 2009-04-25
Boot into a LiveCD, use gparted to shrink /dev/sda1, create a new partition in the empty space and install. ;)

The swap partition should be picked up and used by the other distro you wish to try out.

---

### Post by gibxam on 2009-04-26
Whew... Alright an entire day later I finally have this almost setup properly. I have my Slackware Distro on /dev/sda2 my Ubuntu Distro on /dev/sda1 and my swap on /dev/sda3. This is the output of fdisk /dev/sda:
```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4879        9726    38941560   83  Linux
/dev/sda2               1        4371    35110026   83  Linux
/dev/sda3            4372        4878     4072477+  82  Linux swap

Partition table entries are not in disk order

```
When I boot up my box I get the lilo bootloader and it asks to boot up the Slackware distro but not the Ubuntu one. I know that I have to add the Ubuntu Distro to my /etc/lilo.conf file but I'm not completely sure exactly what I should type in. I'm not sure if because I have 9.04 this should cause anything to be different but I thought I would ask the experts: What lines do I now have to add to my lilo.conf file for me to be able to boot both my Slackware Distro and my Ubuntu Distro?

Many many thanks for helping me this far.

Max

---

