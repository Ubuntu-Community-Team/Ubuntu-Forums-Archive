---
title: "Frets on Fire won't import songs from Guitar Hero world tour (wii)"
date: 2009-03-30
forum: General Help
---

### Post by Dustin2128 on 2009-03-30
I saw the option to import songs from guitar hero, so I popped in the world tour disc, it didn't seem to mount, and It couldn't find a disc in frets on fire. I have a dvd drive, and GHWT is on a dvd

---

### Post by ibuclaw on 2009-03-30
I've never done this, but I'll quote from the site, and interpret it's meaning for you: [http://fretsonfire.wikidot.com/importing-guitar-hero-songs-into-frets-on-fire](http://fretsonfire.wikidot.com/importing-guitar-hero-songs-into-frets-on-fire)

> 
1. Download the OGG Encoder and unzip it. Put the oggenc2.exe into the main folder of your Frets on Fire installation and rename it to oggenc.exe. Also make sure you have at least 1 GB of free space for the songs folder to fill up.

So ... in Linux speak, this means:
```
sudo apt-get install vorbis-tools
```
> 
2. Run Frets on Fire and pick Song Editor > Import Guitar Hero(tm) Songs.

Self Explanitory.
> 
3. Enter the path to your CD drive with the GH disc inserted.

Insert the disc, and set the path as:
```
/cdrom
```
Or so I presume.
> 
4. Wait. It takes at least several hours.

Self Explanitory.

If you are having issues with mounting:
Insert the CD, wait a few seconds, and then type in:
```
dmesg | tail
```
And post the output here. But, if I were to make an assumption. That would be that even though it says **DVD** on the disk, the data is not stored in a standard DVD format that is readable by PC DVD-ROM drives.

Regards
Iain

---

### Post by Helpless noob on 2009-06-15
I have the same problem. When I type dmesg | tail I get this
```
rune@p4-2530:~$ dmesg | tail
[ 2962.379106] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 3344.235231] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 4117.250821] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 4117.254708] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 4293.195607] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 4293.201483] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 4377.683929] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 4377.689690] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 4684.302136] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 4684.307842] sr0: CDROM not ready.  Make sure there is a disc in the drive.

```

---

### Post by Vostrocity on 2009-06-15
FoF can only import songs from Guitar Hero I and II.
[http://fretsonfire.sourceforge.net/documentation/importer/]("http://fretsonfire.sourceforge.net/documentation/importer/")

---

