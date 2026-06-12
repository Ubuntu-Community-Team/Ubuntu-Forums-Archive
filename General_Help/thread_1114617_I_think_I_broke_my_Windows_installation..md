---
title: "I think I broke my Windows installation."
date: 2009-04-02
forum: General Help
---

### Post by Nixie Pixel on 2009-04-02
On this machine I have a 500GB HDD where I have a 100GB NTFS partition, and the rest is partition for linux (20 GB /, a small swap partition, and the rest as /home).  For a while I was running Vista 64 on the 100 GB NTFS partition.  

After purchasing a 60GB SSD and adding it as disk 0 in the system (the 500GB being recognized as disk 1), I swapped the boot order in BIOS and started booting to Windows.  Since I still wanted to dual boot I booted to an Ubuntu Live CD and ran grub, asking it to find stage1 and running root for the HDD and setup.

However it seems that for some reason Ubuntu is seeing my SSD as unallocated space with no partitions, even though I have an NTFS partition with my Vista 64 boot there.  When I try to boot to Vista now in the boot menu grub complains that it can't (I'm not sure of the exact error message).

Is it possible that I somehow deleted the partition without intending to do so?  (I didn't do anything nasty in gparted or fdisk)  Perhaps I just configured grub incorrectly?

Any help would be appreciated.

Thanks!

---

### Post by kanikilu on 2009-04-03
Hi, can you post your /boot/grub/menu.lst file, as well as the output of ```
sudo fdisk -l
```

---

### Post by xenophed on 2009-04-03
kernel don't care what bios thinks as a rule hardware switch them and it should work like it did.Linux can be made to boot from any drive or partition NOT winblows.It always wants to think of it's self as king of the roost.

---

