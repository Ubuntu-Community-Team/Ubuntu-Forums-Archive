---
title: "palm, ogg and linux"
date: 2005-02-25
forum: Desktop Environments
---

### Post by Torrilin on 2005-02-25
I've gotten my palm zire 31 up and running under ubuntu. This is good, since I like having a good backup of my contacts. The other major major thing I use my palm for is playing oggs. In fact, I switched to ogg under windows because it had better support on PalmOS devices *g*.

So, how would I go about using the linux tools for palms to get my oggs onto my palm? I'm getting a bit sick of the Van Halen overload on it at the moment *g*. I can't find enough documentation on the various tools for me to even figure out which one will do the job for me.

edit: through random searching, I found that pilot-schlep (included in the pilot-link package) will send an arbitrary file to your palm, including mp3s and zip files. Alternately, it can pull an arbitrary file from your palm. It's not at all clear whether it can handle dumping the arbitrary file on a SD card tho. I'm getting ideas for more searches tho, so I suppose this is progress.

Kalli

---

### Post by Torrilin on 2005-02-25
Ok, I've done more research. It seems like the best way to transfer the files to and from your palm is to use a separate SD card reader. Not a problem, we have them around. I plug in the card reader (a Stratitec model that handles SD cards along with 4-5 other formats I don't care about) and put my SD card into it. It mounts as sda0 automatically, and I can edit it. The problem comes in when I try wiping the music files off it. They come off easily, but I can't transfer in new ones because it's misreading the card as being ~18 MB (it sees the 5 MB or so of ebooks that are on the card, and 13.8 MB of free space). The card is actually 128 MB. I try removing the card to force it to remount. No joy, in fact, this time it doesn't automatically mount to the desktop. I check dmesg, and the card clearly is mounting, but the GUI isn't showing it correctly. So I get the bright idea to try syncing my palm and *then* try the card again (after an incredulous attempt to force the gui to show me the card by taking it out and reinserting it again). This forced the GUI to show me the card again, this time as sdd1. It still reads as being around ~18 MB, but dmesg shows it as: 

```
USB Mass Storage device found at 50
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
Device not ready.  Make sure there is a disc in the drive.
SCSI device sdd: 244480 512-byte hdwr sectors (125 MB)
sdd: Write Protect is off
sdd: Mode Sense: 02 00 00 00
sdd: assuming drive cache: write through
SCSI device sdd: 244480 512-byte hdwr sectors (125 MB)
sdd: Write Protect is off
sdd: Mode Sense: 02 00 00 00
sdd: assuming drive cache: write through
 /dev/scsi/host1/bus0/target0/lun2: p1

```

This says to me that the OS is seeing the card correctly (the reported size is consistent with what I get when I use my Palm as a jump drive under windows), but the GUI is *not*. 

Once I got it on sdd1, further removal and insertion of the card works fine. It mounts in the GUI and otherwise behaves. So I decide to be evil and check on the card in my palm. It turns out that rather than actually deleting the files, it moved them to a .Trash_emily folder on my card :o. I fix this with TealMover and delete the files for real. I'm now happily dumping new music onto the card, and will check that the silly thing will play the files in a few minutes. So there are a couple problems:

1. A novice user is going to figure when they tell the file manager to delete the files that they really will go away.
2. A novice user is going to be really confused if their SD card sometimes mounts in the gui and sometimes doesn't.
3. Sticking "deleted" files in a hidden directory is confusing since there is no clear way to find out what is wrong under the GUI.

It's actually pretty impressive. This is the worst experience I've had with ubuntu so far... everything else has had very good documentation and has been a piece of cake to solve. Total time expended? About 3 hours. This isn't bad by any stretch, but it could be a lot smoother :).

Kalli

---

