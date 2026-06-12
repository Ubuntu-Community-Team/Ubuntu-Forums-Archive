---
title: "how do i format my ipod to work as a usb drive on ubuntu."
date: 2009-04-19
forum: General Help
---

### Post by Ozzy0sbourne on 2009-04-19
my old 30GB ipod video doesn't keep a good charge (like 20 minutes on a good day.)
i am running ubuntu 8.10 intrepid and i would like to format it to work as a usb drive instead of an ipod.
how do i do this?
thank you in advance ;);)

---

### Post by Svensk023 on 2009-04-19
you can get an app in Add/Remove called gparted, and after you download and install it should be under you System > Administration  as "Partition Editor"

I have never tried reformatting an ipod with it, but I wouldn't see why it couldn't work, so try that out

---

### Post by Ozzy0sbourne on 2009-04-19
> **Svensk023 said:**
> you can get an app in Add/Remove called gparted, and after you download and install it should be under you System > Administration  as "Partition Editor"

I have never tried reformatting an ipod with it, but I wouldn't see why it couldn't work, so try that out

i formatted it to a fat32... now it detects as usb drive ;]
i love you XD (jk)
but still thanks. :D
im going to see if the "intended" operation will work and then ill post the results on here :]

---

### Post by Svensk023 on 2009-04-19
glad to help!

enjoy :D

---

### Post by Ozzy0sbourne on 2009-04-19
> **Svensk023 said:**
> glad to help!

enjoy :D

i regret to say that it comes up with this error message when i try to access or use the files.


Unable to mount location:

Can't mount file

---

### Post by Ozzy0sbourne on 2009-04-19
now it says its a SCSI Drive WTF!?

---

### Post by Svensk023 on 2009-04-19
> **Ozzy0sbourne said:**
> now it says its a SCSI Drive WTF!?

thats fine, its just not detecting it as an "ipod" anymore.

as for your mount problems, try to unmount it using gparted. then unplug and re-connect it. 

if that dosent work, we can take it from there

---

### Post by Ozzy0sbourne on 2009-04-19
> **Svensk023 said:**
> thats fine, its just not detecting it as an "ipod" anymore.

as for your mount problems, try to unmount it using gparted. then unplug and re-connect it. 

if that dosent work, we can take it from there
 
ok now it reads it as 29.9GB media!!! and i can open it too... and now im putting the item on it.

im going to let the huge file transfer, then ill restart my computer and tell you if it works =]

---

### Post by Svensk023 on 2009-04-19
Alrighty!


Just as a random fact I learned the hard way, FAT32 has a single-file size restriction of 4GB, so if you were to try and transfer a HDDVD or something, it wont work. So for bigger extrernal HDD's I usually just reformat it to NTFS, because it will be readable by both Linux and Windows computers, but sadly Mac's are left out of the loop

---

### Post by Ozzy0sbourne on 2009-04-19
> **Svensk023 said:**
> Alrighty!


Just as a random fact I learned the hard way, FAT32 has a single-file size restriction of 4GB, so if you were to try and transfer a HDDVD or something, it wont work. So for bigger extrernal HDD's I usually just reformat it to NTFS, because it will be readable by both Linux and Windows computers, but sadly Mac's are left out of the loop

F i just read the post after it only transfered 4 GB xD
fail

---

### Post by Ozzy0sbourne on 2009-04-19
> **Svensk023 said:**
> Alrighty!


Just as a random fact I learned the hard way, FAT32 has a single-file size restriction of 4GB, so if you were to try and transfer a HDDVD or something, it wont work. So for bigger extrernal HDD's I usually just reformat it to NTFS, because it will be readable by both Linux and Windows computers, but sadly Mac's are left out of the loop

the NTFS option is greyed out? :[ will ext3 or ext2 work?


EDIT!!!!!!!!!!: i got ntfs to work with (sudo apt-get install ntfsprogs)

now ima restart my computer and see if it did anything

---

### Post by Svensk023 on 2009-04-19
you can enable NTFS partitioning by going into an open terminal and input the following.

```
sudo apt-get install ntfsprogs
```

that should give gparted the ability to format in NTFS

---

