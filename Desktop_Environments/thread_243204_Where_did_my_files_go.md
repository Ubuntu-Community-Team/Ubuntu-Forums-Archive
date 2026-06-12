---
title: "Where did my files go?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Regenerate on 2006-08-24
Hi guys,

Working with Ubunt for a month now and I'm really liking it (comming from the Redmond commercial package).
Today I wanted to make a backup from my personal files, but before doing so I rearanged the folders and files so I could make a neat orderly backup. The problem now is that all folders I rearanged ar empty (the folders I didn't rearange still contain files)! When I look at the properties of the folders, they are no more then a few kB's so they really seam to be empty. I rebooted to see if that would help but it didn't. I also checked the size of the home folder (wich holds all files) but that still seems to be what it was (around 32GB).

System info:
[LIST]
[*]Latest Kubuntu 6.06 version
[*]80 GB IDE disk (hda1) with the 3 standard linux partitions
[*]250 GB SATA disk (sda1) with one partition, XFS-SGI's journaling filesystem filesystem (this is the disk the files are (or were...) on.
[*]
[/LIST]

Any suggestions about what might have happend to my files?

Thanks in advance!

---

### Post by croak77 on 2006-08-24
Do you know a name of a file you are missing? If you do, open a terminal:

```
sudo updatedb
```
```
slocate file
```

It should list the path to the file(s) that match. If you dont; have slocate installed, try it with locate.

---

### Post by peabody on 2006-08-24
Hmm, if all else fails, check the lost+found foulder on / and /home

---

### Post by Regenerate on 2006-08-25
Hi,

Thanks for the suggestions. I tried a couple of filenames with the slocate command that doesn't seem to help me. The lost+found folder on hda1 looks empty, and there is no lost+found folder on the sda1 disk...

So I'm still looking for my files... :(

---

### Post by Regenerate on 2006-08-26
Well, not making progress here :(. Any more suggestions on how to reach my data?

---

### Post by peabody on 2006-08-27
From a gnome-terminal try this:

sudo find /home -name 'filename you remember'

That will recurse the entire home folder looking for a a file with that name.

---

