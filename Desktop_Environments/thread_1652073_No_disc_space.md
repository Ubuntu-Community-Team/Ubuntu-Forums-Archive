---
title: "No disc space"
date: 2010-12-24
forum: Desktop Environments
---

### Post by Chris62 on 2010-12-24
Hi,

I have a double-boot Windows/Ubuntu desktop machine to which my brother has added Fedora. It has 2 hard drives with Windows on one and Ubuntu on the other. Unfortunately Fedora seems to have taken practically all the space on the second hard drive (which contains Ubuntu 10.10) and there is now only 10 Mb space for Ubuntu, which means that Ubuntu cannot be updated from time to time. Is there a way of reducing the amount of disc space that Fedora has claimed and giving it back to Ubuntu.

I am told that when Fedora was being installed, the option to shrink the space occupied by Ubuntu was used. The disc in question has a capacity of 80 GB and as mentioned above, it only contained Ubuntu 10.10 so I don't understand why Ubuntu has been shrunk so  that it only has 10 MB to use.

---

### Post by 3Miro on 2010-12-24
Boot from a LiveCD and use Gparted to see what is happening. Fedora should have created its own partition, but not taken all the space form Ubuntu. Check the partition layout and from Gparted you can move/resize partitions.

MAKE SURE TO BACKUP ALL IMPORTANT STUFF FROM THE HDD. PLAYING WITH PARTITIONS CAN DESTROY ALL DATA ON IT.

---

### Post by ranahannan on 2010-12-24
:Dtry to install xp crystal;)

---

### Post by Chris62 on 2010-12-26
Hello 3Miro,

Thanks for your reply. I did what you suggested but have to confess I don't know what to do with the output. I tried to copy it here but wasn't able to.

However, the output from gparted says that:

/dev/sdb1 is ext4 and occupies 2.93 Gb of which 2.78 Gb are used
/dev/sdb3 is ext4 and occupies 500 Mb of which 62.76 have been used
/dev/adb4 is lvm2 and occupies 68.15 Gb none of which appear to be in use. It has an exclamation mark beside it
/dev/sdb2 is extended and is 2.93 Gb
/dev/sdb5 is linux-swap and is 2.93

I don't know what this lvm2 is - it wasn't there before Fedora 14 was installed and I don't know the significance of the exclamation mark beside its entry in the gparted output.

Does any of this make sense to you? Presumably I could expand the partition for Ubuntu by shrinking the lvm2 partition?

When I boot into Ubuntu I get a message to say that there is very little disc space left but the amount of space is different each time I boot.

---

