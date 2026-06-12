---
title: "Creating a Jaunty Hard Drive Image"
date: 2009-06-05
forum: General Help
---

### Post by jlacroix on 2009-06-05
Hello,

I have Acronis True Image 11 and Clonezilla, and those are the two I use to clone my PC's. Unfortunately, I don't think Acronis supports EXT4 and Clonezilla seems to want to image the entire drive, and doesn't seem to support exceptions.

Let me explain what I mean. I have a ton of data in my videos, music and pictures directories in my home folder. I prefer to exclude those folders from my image, otherwise the image would be huge. I *do* want all the other folders in /home, though. I want to do this so I can restore my hard drive if I need to.

Is there an easy way to do this? Acronis supports all of those features but it doesn't support Linux as much. :(

---

### Post by Krupski on 2009-06-05
> **jlacroix said:**
> Hello,

I have Acronis True Image 11 and Clonezilla, and those are the two I use to clone my PC's. Unfortunately, I don't think Acronis supports EXT4 and Clonezilla seems to want to image the entire drive, and doesn't seem to support exceptions.

Let me explain what I mean. I have a ton of data in my videos, music and pictures directories in my home folder. I prefer to exclude those folders from my image, otherwise the image would be huge. I *do* want all the other folders in /home, though. I want to do this so I can restore my hard drive if I need to.

Is there an easy way to do this? Acronis supports all of those features but it doesn't support Linux as much. :(

If you want to image an entire hard drive onto another hard drive (and they should be the same size), you can do this (assuming your boot drive is "/dev/sda" and the destination for the copy is "/dev/sdb"):

```

[B][COLOR="Red"]
### WARNING - SAMPLE CODE - DO NOT EXECUTE THIS ###
### UNLESS YOU KNOW EXACTLY WHAT YOU ARE DOING! ###
[/COLOR][/B]

dd if=/dev/sda of=/dev/sdb bs=64K

[B][COLOR="Red"]
### WARNING - SAMPLE CODE - DO NOT EXECUTE THIS ###
### UNLESS YOU KNOW EXACTLY WHAT YOU ARE DOING! ###
[/COLOR][/B]

```

This will copy, byte for byte, everything from /dev/sda onto /dev/sdb... including the partition table, the master boot record, the directory structure... everything. 

Note that the destination drive should be the same as the source since drive geometry information (located in the partition table) will also be copied.

A better way to go is to have Linux installed on either a tiny and separate hard drive or, better, on a solid state drive.

What I do is take a 4 GB compact flash card (a camera card) and install it into a CD to IDE adapter board ([[COLOR="Blue"]**LINK**[/COLOR]]("http://www.addonics.com/products/flash_memory_reader/adebidecf.asp")) then just plug it into the motherboard IDE connector.

The hard drives are connected to SATA ports, setup as RAID and have ONLY data on them. All of the operating system is on the compact flash card.

Since it's only 4 GB (and since Linux takes up less than 2 GB), making backup images is easy. I use DD to make a 4GB image of the card, then GZIP to compress it into about a 600K file.

If I ever "screw up" something, I can just take the last known good image, copy it back to the flash card and be back up and running in 5 minutes.

Lastly... if you want to only backup parts of your drive, why not just use the CP command? With the -p and -r switches (preserve attributes and recursive, respectively), you can go to a particular directory and copy everything in it and below to a destination.


Hope this helps...

-- Roger

---

### Post by jlacroix on 2009-06-05
> **Krupski said:**
> If you want to image an entire hard drive onto another hard drive (and they should be the same size), you can do this (assuming your boot drive is "/dev/sda" and the destination for the copy is "/dev/sdb"):

```

[B][COLOR="Red"]
### WARNING - SAMPLE CODE - DO NOT EXECUTE THIS ###
### UNLESS YOU KNOW EXACTLY WHAT YOU ARE DOING! ###
[/COLOR][/B]

dd if=/dev/sda of=/dev/sdb bs=64K

[B][COLOR="Red"]
### WARNING - SAMPLE CODE - DO NOT EXECUTE THIS ###
### UNLESS YOU KNOW EXACTLY WHAT YOU ARE DOING! ###
[/COLOR][/B]

```

This will copy, byte for byte, everything from /dev/sda onto /dev/sdb... including the partition table, the master boot record, the directory structure... everything. 

Note that the destination drive should be the same as the source since drive geometry information (located in the partition table) will also be copied.

A better way to go is to have Linux installed on either a tiny and separate hard drive or, better, on a solid state drive.

What I do is take a 4 GB compact flash card (a camera card) and install it into a CD to IDE adapter board ([[COLOR="Blue"]**LINK**[/COLOR]]("http://www.addonics.com/products/flash_memory_reader/adebidecf.asp")) then just plug it into the motherboard IDE connector.

The hard drives are connected to SATA ports, setup as RAID and have ONLY data on them. All of the operating system is on the compact flash card.

Since it's only 4 GB (and since Linux takes up less than 2 GB), making backup images is easy. I use DD to make a 4GB image of the card, then GZIP to compress it into about a 600K file.

If I ever "screw up" something, I can just take the last known good image, copy it back to the flash card and be back up and running in 5 minutes.

Lastly... if you want to only backup parts of your drive, why not just use the CP command? With the -p and -r switches (preserve attributes and recursive, respectively), you can go to a particular directory and copy everything in it and below to a destination.


Hope this helps...

-- Roger

Your information was very helpful and I will definitely save it for future reference, but its not exactly what I am looking for. (One of the machines is a laptop). However, the camera card idea is very clever actually but my laptop wouldn't be able to benefit from that. :(

Let me explain further how I am set up. I two computers (a laptop and a desktop) as well as an external hard drive. I use Unison to sync my laptop, desktop, and external hard drive so that they all have the same files. This essentially backs up folders such as Videos and Music on all three.

Also on the external hard drive is an images folder. I store hard drive images of various machines on it. If ever something happens to my drive (I am constantly testing things) I want to be able to restore from the image. There is no point for me to include folders such as Videos or Photos in my image, because that is redundant. I would use Clonezilla to do this, but it will grab the entire drive (including the Windows partition and the folders I already back up). Also, Clonezilla doesn't support EXT4 yet, unfortunately.

---

### Post by blueridgedog on 2009-06-05
Look into remastersys.  It may have the option to exclude files.  I use it, but I have my home directory mounted as a separate drive that I just unmount before running it.

---

### Post by jens-mct on 2009-06-11
thx for the intel, i'm going to give U9 a try when my exams finish, hopefully this kind of backup will work

a shame though, ext4 is more performant than ext3 i heared, but now i've lost the acronis image backup option :(

---

### Post by jens-mct on 2009-06-29
> **jlacroix said:**
> Hello,

I have Acronis True Image 11 and Clonezilla, and those are the two I use to clone my PC's. Unfortunately, I don't think Acronis supports EXT4 and Clonezilla seems to want to image the entire drive, and doesn't seem to support exceptions.

Let me explain what I mean. I have a ton of data in my videos, music and pictures directories in my home folder. I prefer to exclude those folders from my image, otherwise the image would be huge. I *do* want all the other folders in /home, though. I want to do this so I can restore my hard drive if I need to.

Is there an easy way to do this? Acronis supports all of those features but it doesn't support Linux as much. :(
i've just testet [http://clonezilla.org/](http://clonezilla.org/) and it also supports partition imaging aswell (ext4 and ntfs included)
to all those who seek a free alternative with wizard based gui I recommend clonezilla

---

### Post by jlacroix on 2009-06-29
> **jens-mct said:**
> i've just testet [http://clonezilla.org/](http://clonezilla.org/) and it also supports partition imaging aswell (ext4 and ntfs included)
to all those who seek a free alternative with wizard based gui I recommend clonezilla

Clonezilla is good, though I don't remember an option the last time I used it to save a partition and not the entire disk. If there is an option I must have missed it.

I feel it would be better if I Clonezilla could skip directories. I don't need my Music and Videos as part of the image because I already back those up elsewhere.

---

