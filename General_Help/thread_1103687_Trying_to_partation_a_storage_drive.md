---
title: "Trying to partation a storage drive"
date: 2009-03-22
forum: General Help
---

### Post by AND_YOU_ARE on 2009-03-22
I am very new to Ubuntu and the Linux OS in general.  I am genuinely trying to give Ubuntu a shot as a primary OS.  Currently I have two 320GB drives, one for Win XP, and the other for Ubuntu.  I also have two 1.5TB drives.  I set one up as NTFS in XP for my files not knowing that Ubuntu can only read from it.  So I am trying to figure out how to format the other drive in FAT32 for a shared storage volume.  

What I have figured out so far is the following; install gparted, and find the drive in question.  I have the 1.36TB unallocated.  However I am falling on my face when trying to get it a FAT32 partition installed.

I am trying this:
- New, create new partition, primary partition, FAT32 filesystem and a lable of 'Shared Storage'.  Click Add, then Apply.  Then I am told an error occurred while applying the operations.

So unless I am missing something basic, I am stuck.

Any help is appreciated, and feel free to spell it out, do to my inexperience with Ubuntu.

---

### Post by bumanie on 2009-03-22
Hmm...Firstly ubuntu can read and write to ntfs, so a FAT32 partition is not really necessary. As for why gparted is not working - not sure, your description would indicate you doing things correctly. If you are using the gparted in ubuntu, try downloading the gparted live cd and see if that does any better, but as I stated linux/ubuntu does or should read and write to NTFS very well, this has been a stable feature for some time now via [ntfs-3g]("http://www.ntfs-3g.org/").

---

### Post by AND_YOU_ARE on 2009-03-22
Hmmm.  I was told that FAT32 is best for a shared storage drive between Ubuntu and Windows, and that Ubuntu doesnt write to NTFS.  I guess I can write to the NTFS drive.  I didnt try before.  

On a similar note, do non Ubuntu system drives always need to be mounted and show up on the desktop?  Personally I prefer a clean desktop with the use of a dock.

---

### Post by KeyserSoze93 on 2009-03-23
> **AND_YOU_ARE said:**
> Hmmm.  I was told that FAT32 is best for a shared storage drive between Ubuntu and Windows, and that Ubuntu doesnt write to NTFS.  I guess I can write to the NTFS drive.  I didnt try before.  

On a similar note, do non Ubuntu system drives always need to be mounted and show up on the desktop?  Personally I prefer a clean desktop with the use of a dock.

Ubuntu can deal fine with NTFS (I used that to share a drive/partition before I got rid of Windows), and NTFS is probably better for big drives (not sure what sizes your talking about allocating, but you have some rather large hard drives there)

I'm not sure if gParted cares, but Windows will not format a FAT32 drive bigger than 32 GB, as far as I know.

---

### Post by AND_YOU_ARE on 2009-03-23
Alright, so I'll keep both 1.5TB drives as NTFS.

My other question remains.  When these drives are mounted, they show up on the desktop.  Is there a way to change where these show up?  I prefer to keep the desktop clean.

---

### Post by drs305 on 2009-03-23
> **AND_YOU_ARE said:**
> Alright, so I'll keep both 1.5TB drives as NTFS.

My other question remains.  When these drives are mounted, they show up on the desktop.  Is there a way to change where these show up?  I prefer to keep the desktop clean.

You can mount them to a location other than /media . Devices mounted to /media show up on the desktop.

If you want the desktop to be *completely* empty, you can turn it off entirely with:
```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'false'

```

---

