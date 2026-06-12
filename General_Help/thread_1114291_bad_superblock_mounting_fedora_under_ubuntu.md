---
title: "bad superblock? mounting fedora under ubuntu"
date: 2009-04-02
forum: General Help
---

### Post by natelienn on 2009-04-02
Hello all, I have been using Fedora 10 for some time now, and have recently come to a problem. I believe this may have something to do with the fact that I was playing very loud music right next to my laptop causing my hard drive to skip or something. Anyway, when I turn on the laptop, The very first thing printed is something close to the following:

ata1: hard resetting link
ata1: link is slow to respond, please be patient (ready=0)
..
..
sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sda, sector 565185
JBD: Failed to read block at offset 18832
sd 0:0:0:0: [sda] READ CAPACITY failed
...
..
Ext3-fs: error loading journal
mount: error mounting /dev/root on /sysroot as ext3: Invalid argument


So anyway it appears that there's a bad sector and the system will not boot. So I popped in the live ubuntu CD, hoping to get my files back. I following the instructions via [http://linux-sxs.org/storage/fedora2ubuntu.html](http://linux-sxs.org/storage/fedora2ubuntu.html) and all works except the very last step. When I try to mount, I get  this error:

sudo mount /dev/VolGroup00/LogVol00 /mnt/fcroot -o ro,user
mount: wrong fs type, bad option, bad superblock on /dev/mapper/VolGroup00-LogVol00,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I don't know what else to do. Is there some way to scrap the files that are corrupt and get the rest back? Are there any options here? The files I had were very important, I want to do all possible to get them back. Thanks for any help

---

### Post by natelienn on 2009-04-02
Sorry to bug you guys, but I am still stumped. I have been searching threads on ways to access this, but can't seem to find anything. If I can't figure it out by tomorrow I must wipe my hard drive, and I really don't want to do that. Thanks for any help

---

