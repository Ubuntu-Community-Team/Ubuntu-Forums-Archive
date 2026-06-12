---
title: "XFS missing data"
date: 2009-06-09
forum: General Help
---

### Post by chimpoko on 2009-06-09
Hello,

I just bought and installed a 1 TB Drive into my mythbuntu installation, and  was copying all my data from 3 different XFS drives to the new 1 TB XFS drive. I could verify the data being copied for the first few drives, as I was only copying from one drive at a time, but then on the 3rd drive I left copying overnight, and what I found this morning is I cannot see any of the data on the drive. just . .. and .trash
I do a df -h /dev/sdc1 and it returns 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             932G  447G  485G  48% /mnt/data
```

it seems that all the data is there as it is being "used"

I have tried the following;

unmounting and remounting
rebooting the server

I don't know what to do to revive my data, and I didn't want to proceed blindly on my own and find out what i did just messed things up even more.
can someone with experience or knowledge in XFS help me with this?

Thank you,
Chimpoko

---

### Post by Tuvok41 on 2009-06-09
Well I'm having somewhat the same problem, I lost 2 huge folders on my external usb drive, the same as chimpoko the data seems to be in used but I cant see them, is there anything that can do the same thing in ubuntu like GetDataBack for NTFS, I really don't want to have to install windows just to retrieve this, surely there has to be some way to do the same without having to copy the whole drive, its 750gb and I only need to recover 360Gb of data that's sitting somewhere in it, the rest is not completely full but the rest of the data on it is accessible and everything.

---

### Post by chimpoko on 2009-06-09
Tuvok41

was there more than 2 folders in your external USB disk ? 
or did it consist of more but only 2 of the folders became missing ?

I'm trying out a defrag of the drive... I highly doubt it will do anything, but it's worth a shot...

---

### Post by Tuvok41 on 2009-06-09
Well in my case what happened could be of two things, at that time I had some problems with the usb port and it would at times make it go un-mounted then come back as another disk, so if it was disk_0 it would then come back as disk_1 but the disk_0 was still there and nothing I could do to remove or un-mount it. I had more than those 2 folders in the folder they were in. But those 2 folders were 2 huge torrents I was dling and had many files in it completed, so a few times it happened while I was afk and when i came back i notice they were in red in my utorrent so I checked it out but since i was unable to remove disk_0 from the pool, I had to reboot and then the bittorrent client started to check the files, took a long *** time as one is about 160Gb and the other was 200GB, wasn't really getting everything in there but around 60% for each I will say. They both checked out nicely tho that time. Next day same thing happen, rebooted, and when i restarted the client again it started to check them, since it takes a while to go all through I went afk, came back 2 hours later and saw it was hashing the second torrent, went afk again came back and again the drive un-mounted and remounted itself and I presume as i cant be certain it was completed or not, that it happened while checking that torrent. Anyhow after rebooting again, both folders were gone!
I re-added the torrent file in the client again and it started to check the files and the folders came back and some files too, only 1 complete in 1 and the other i have like 75% of 1 file, it's like it could see that but fail to find the rest. But its there alright im missing over 300Gb in space as the total data on the drive that I can access will not match the amount of space I should have left if these 2 folders were completely deleted. So I guess the situation had to be a bit different then yours but the end result is the same, it there, its inaccessible therefor, I dont think anything is lost but when I had similar problems with windows I would run GetDataBack for NTSF and I would retrieve what I had lost, I just dont wanna have to install windows again so please if someone knows how to achieve the same thing with ubuntu, I would greatly be thankful.

---

### Post by vahnx on 2009-06-09
If you have SpinRite, try that. I heard it works wonders.

---

### Post by Tuvok41 on 2009-06-09
The only thing it is for windows XP and I am trying to avoid to install winshit, I already have GetDataBack for NTFS that has work wonders for me in the past, 100% success to date. I need something that runs on linux, I doubt wine could handle and run this type of software flawlessly.

P.S.: A big thank you for the reply, all help is appreciated!

---

### Post by chimpoko on 2009-06-10
vahnx

Thank you for your reply, all help is appreciated.
I am attempting this on a 1TB drive, so it's gonna take a while...
I just started the recovery mode process

I'll update when it's done.. probably later today or even tommorow :o

---

### Post by chimpoko on 2009-06-11
spin rite didn't like my 1TB drive...
it kept giving me an error that is common on large drives or dual processors, I'm out of luck with spinrite from what it seems...


any-other ideas ?

thanks

---

### Post by chimpoko on 2009-06-13
anyone have any ideas ?

---

### Post by chimpoko on 2009-07-06
I have found my data!!!!
yes! it's true!

UFS Explorer is what I used, and as I type this, my data is slowly being recovered!
all my data was found in the .Trash-0 folder which is hidden and which I cannot access, even when root!

---

### Post by Tuvok41 on 2009-08-14
> **chimpoko said:**
> I have found my data!!!!
yes! it's true!

UFS Explorer is what I used, and as I type this, my data is slowly being recovered!
all my data was found in the .Trash-0 folder which is hidden and which I cannot access, even when root!
Is this a linux program or windows?

---

