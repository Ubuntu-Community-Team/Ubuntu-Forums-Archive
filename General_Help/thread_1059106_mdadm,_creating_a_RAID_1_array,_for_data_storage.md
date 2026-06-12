---
title: "mdadm, creating a RAID 1 array, for data storage"
date: 2009-02-03
forum: General Help
---

### Post by stuartmumford on 2009-02-03
Hello,

I am pretty new to linux and ubuntu, I have a mini-itx mb and a pci sata controller, wich is 'fakeRAID', then 2 1TB drives that I would like to put into a Raid 1 array.

After some research I have given up on 'fakeRAID' because the software raid looked easier!(hahaha)

What I am trying to do is create an array with mdadm, I use the 
```
sudo mdadm --create --level=1 --raid-devices=2 /dev/sda /dev/sdb
``` command and the responce I get is
```
mdadm: Cannot open /dev/sda1: Device or resource busy
```
then I get this for sdb1 as well and then it aborts creating the raid.

I ran the live cd and managed to set up a array there, but it wouldn't format properly.

Any help would be nice as I am about ready to explode!

(btw using ubuntu 8.04 LTS)

---

### Post by fjgaude on 2009-02-03
Make sure you have the correct command to create the array:

```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda /dev/sdb
```

Are you sure you are wanting to use the whold disk, i.e., sda and sdb, and not sda1 and sdb1?

The error implies that the drives are busy and likely part of another array. If you tried before and created an array and started over you likely will have to zero the superblocks before going on:

```
sudo mdadm --zero-superblock /dev/sda
```

Or is it /dev/sda1? Do that for both drives.

You might find these links useful:

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

[http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing](http://linux-raid.osdl.org/index.php/Detecting%2C_querying_and_testing)

[http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)

Let us know how you are doing.

---

