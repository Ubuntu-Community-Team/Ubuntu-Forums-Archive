---
title: "File Storage Issue"
date: 2009-01-01
forum: General Help
---

### Post by Mark_25 on 2009-01-01
Hi all wondered if anyone has a solution to this? I'm moving over from Windows XP to using Ubuntu permanently, I've got used to all the diferent apps and the OS now.

My problem is this:

- I have two windows XP hard discs - One for Windows and files (OS) / One for music storage and iTunes [H:].

- I have an ubuntu partition which I believe uses two seperate partitions again.

- The ubuntu section of space on the hard disk is pretty much full now, whereas I have about 80Gb free on my Windows XP hard disk [C:]. However when I download new stuff onto my Ubuntu desktop it fails and tells me I don't have enough memory.

- Ideally I want to store all my files on ubuntu in the 'Documents' folder built in there and download all new files to my desktop until they're sorted.

- I also have all my mp3's in H:/My Music/iTunes/iTunes Music and those folders have all been imported into Rhythmbox music player, not sure whether it's duplicating files and also I may consider reformatting the [H:] drive and use Rhythmbox to manage the files. That's not too important for now but any help is greatly appreciated.

---

### Post by Elfy on 2009-01-01
IT sounds like you need to have a session with a partition editor :)

Firstly though there's no need to move files from a ntfs partition as you can set it up to be read and write.

Unfortunately using windows names for drives doesn't give us much info - H:\ might or might not be on a differnt hard drive :)

Open a terminal and run this

```
sudo fdisk -l
```

Post the output here and we'll be able to help more.

Certainly there's nothing to stop you deleting and resizing partitions, but it might be better to create new partitions with the deleted space.

---

### Post by Mark_25 on 2009-01-04
Here you go, cheers.

>  
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       15216   122214487+   f  W95 Ext'd (LBA)
/dev/sda2   *       15217       21744    52436160    7  HPFS/NTFS
/dev/sda3           21745       24167    19462747+  83  Linux
/dev/sda4           24168       24321     1237005   82  Linux swap / Solaris
/dev/sda5               2       15216   122214456    7  HPFS/NTFS
mark@mark-desktop:~$ 


Sorry about the late reply, had a problem with spyware on my other PC and with New Year etc got a bit delayed.

---

### Post by Elfy on 2009-01-04
Personally I would use the partition editor on the livecd to delete and then create a ext3 partition in the unallocated space. Then mount that partition in my ubuntu install with fstab.

If you wanted to then you could move the data from the ntfs which you call H:\ and do the same.

Alternatively you could resize your / partition

Edit - it doesn't appear to me that you have an 80Gb drive for your xp install there - but I could be working it out wrong.

---

