---
title: "Just for looks..."
date: 2010-01-03
forum: Desktop Environments
---

### Post by Cariboo1938 on 2010-01-03
on my Desktop Computer I have two Harddrives, one of them is totally used for Ubuntu Linux. The second HD is partially used for  Windows XP, and I use the rest of it (with an ext3 filesystem) for Linux too. When mounted it appears on the desktop as "62.4 GB Media" and I wonder if I could change this name?
See attachments

---

### Post by SalahTr on 2010-01-05
[https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by Cariboo1938 on 2010-01-12
Thanks SalahTr for the link...
I was not successful though, because I couldn't find the the "Label" button as it is described in the guide...
it looks this only works for USB drives but not for my hard drives, am I right?
I attached several screenshot showing what I did so far

---

### Post by sisco311 on 2010-01-12
Open a terminal (Applications -> Accessories -> Terminal)
and run:
```
sudo e2label /dev/sdb5 **label**
```
to change the label of the ext3 partition. Replace **label** with the actual label.

to change the label of an NTFS partition:
```
sudo ntfslabel **/dev/sdXY** **label**
```
replace **/dev/sdXY** with the device name listed in gparted.

---

### Post by Cariboo1938 on 2010-01-12
> **sisco311 said:**
> Open a terminal (Applications -> Accessories -> Terminal)
and run:
```
sudo e2label /dev/sdb5 **label**
```
to change the label of the ext3 partition. Replace **label** with the actual label.


OK...Labeling worked fine, I labeled sdb5 as LinuxPart. 
But sorry, this is not what I wanted and I apologize for being not specific enough in the first place.
I want to change the name of this partition as it shows under 
--->Main Menu --->Places...see attached screenshots.
Thanks, sisco311, for the help...

---

### Post by sisco311 on 2010-01-12
> **Cariboo1938 said:**
> OK...Labeling worked fine, I labeled sdb5 as LinuxPart. 
But sorry, this is not what I wanted and I apologize for being not specific enough in the first place.
I want to change the name of this partition as it shows under 
--->Main Menu --->Places...see attached screenshots.
Thanks, sisco311, for the help...

Did you try to log out and log back in and/or remount the partitions. If the partitions is labeled the label of the partition should be displayed.

---

### Post by Cariboo1938 on 2010-01-12
> **sisco311 said:**
> Did you try to log out and log back in and/or remount the partitions. If the partitions is labeled the label of the partition should be displayed.
No I didn't yet, one moment...
:D Yeah...It's done...Thank you very much...learned another lesson...:D

---

