---
title: "Partitioning another drive question"
date: 2009-02-04
forum: General Help
---

### Post by Metallicaman41 on 2009-02-04
First let me say I am a windows user, but I can work my way around the unix shell and linux if needed.

I just installed Ubuntu 8.10 server onto my computer with the full gnome desktop installed.

I have 2 different drives (1 raid 0 array 2x80gb sata, 1 160gb pata drive) I would like to format the pata drive to fat32 and use the entire disk for a fileshare area.

I went through a couple installs and the pata drive is a mess with linux and windows partitions on it.

I opened Gparted(gnome partition manager) to format the pata and recieved the following error.

[QUOTE]The kernal is unable to re-read the partitiontables on the following devices - dev/mapper/pdc_bhdegahbaj1 because of this you will only have limited access to these devices.  Unmount all mounted partitions on a device to get full access./QUOTE]

After I close out the error I can see the following in the partition drop down.

I have the following drives listed in the drop down
dev/mapper/pdc_bhdegahbaj (149.06 GiB)
dev/mapper/pdc_bhdegahbaj1 (142.97 GiB)
dev/mapper/pdc_bhdegahbaj5 (6.06 GiB)
dev/sda (74.53 GiB)
dev/sdb (74.53 GiB)
dev/sdc (149.05 GiB)

My question is Gparted the program I want to be using and how should I go about formating that pata drive, Im not sure how to tell what is the pata drive and whats the raid array.  This is a fresh install, so Im willing to write zeros to all my drives and reinstall unix if thats the easier way to clean up the partitions.

---

### Post by blazemore on 2009-02-04
Could you please post the output of ```
sudo fdisk -l
```

Please enclose it in [ code] tags

---

### Post by Metallicaman41 on 2009-02-04
The output was

```
Unable to seek on /dev/sda
```

---

### Post by blazemore on 2009-02-04
Is that it???

---

### Post by Metallicaman41 on 2009-02-04
Yea thats all that is output.

---

### Post by blazemore on 2009-02-04
Have you tried booting off the LiveCD and doing your partitioning from the Partition Editor on there?

---

### Post by Metallicaman41 on 2009-02-04
nope. I will give that a try now

---

### Post by Metallicaman41 on 2009-02-04
That worked.  When the live CD was booted it wasnt able to read the Raid array properly, so all I could see in the partition editor was 2 x 80gb drives and the 160 that i wanted to format.

Oddly running sudo fdisk -l still gave the same results as previously.

---

