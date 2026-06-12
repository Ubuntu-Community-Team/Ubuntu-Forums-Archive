---
title: "How to completly clean a old hard drive?"
date: 2009-01-03
forum: General Help
---

### Post by Maxxtsch on 2009-01-03
How would I reformat a old ex-OS9 hard drive from my desk top on Ubuntu?

---

### Post by |{urse on 2009-01-03
if you want it totally wiped before you let ubuntu's partitioner at it: 

[http://www.dban.org/](http://www.dban.org/)

this is a link to a livecd used to permanantly delete all data from a hard drive. 

-and/or-

just pop in the ubuntu disk and follow the prompts. remember to select manual partitioning and choose 100% allocation for ubuntu.

---

### Post by |{urse on 2009-01-03
your avatar says "**** bear" on it. Does that have anything to do with needing to "completely clean" that hard drive?

lol

---

### Post by stderr on 2009-01-03
I would use Kurse's solutions (or similar ones) in preference to what I'm about to suggest; this is more for informational purposes.

This is to wipe all data on a HDD by overwriting the whole thing. If you're not worried about security in the sense of leaving your old data behind on the drive, then you can simply format it.

You could umount the drive and use the dd command to write zeros (or pseudorandom numbers) over the entire drive. You absolutely have to get the correct device (for of=, i.e. you may not and probably don't want to blank /dev/sda1), or you'll be irretrievably blanking valuable data :|

So beware: dd has a nickname as "Disk Destroyer" as it's very easy to blank the wrong device :)

Fill with zeros:
```
dd if=/dev/zero of=/dev/sda1 bs=1M
```
Fill with pseudorandom data:
```
dd if=/dev/urandom of=/dev/sda1 bs=1M
```

The command reads "copy input file /dev/[whatever] to output file /dev/[whatever], by copying 1MB at a time (the blocksize)".

Alternatively you could use the shred command... and many others.

edit: Like I say, if you're at all unsure about the /dev to put under of=/dev/[whatever], ask, just make sure you don't blank the wrong thing!

---

### Post by Kinney on 2009-01-04
> **stderr said:**
> I would use Kurse's solutions (or similar ones) in preference to what I'm about to suggest; this is more for informational purposes.

This is to wipe all data on a HDD by overwriting the whole thing. If you're not worried about security in the sense of leaving your old data behind on the drive, then you can simply format it.

You could umount the drive and use the dd command to write zeros (or pseudorandom numbers) over the entire drive. You absolutely have to get the correct device (for of=, i.e. you may not and probably don't want to blank /dev/sda1), or you'll be irretrievably blanking valuable data :|

So beware: dd has a nickname as "Disk Destroyer" as it's very easy to blank the wrong device :)

Fill with zeros:
```
dd if=/dev/zero of=/dev/sda1 bs=1M
```
Fill with pseudorandom data:
```
dd if=/dev/urandom of=/dev/sda1 bs=1M
```

The command reads "copy input file /dev/[whatever] to output file /dev/[whatever], by copying 1MB at a time (the blocksize)".

Alternatively you could use the shred command... and many others.

edit: Like I say, if you're at all unsure about the /dev to put under of=/dev/[whatever], ask, just make sure you don't blank the wrong thing!

Just one question. I noticed that you are specifying a partition in the output. Would this work the same if I just used /dev/sdd since I've already deleted all of the partitions in fdisk?

---

### Post by oneadvent on 2009-01-04
You can delete whatever "files" you need to remove, either by partition or by simply deleting them, and then use bcwipe to do a government scan on the free space.

That is a free tool you can download, just google it. It is native for linux.

BTW: you would have better luck getting help in here without that ****bear being your image choice. You will turn off a lot of good help, even if you think its funny.

---

### Post by hundredwatt on 2009-01-04
This should work fine for any civilian purposes.
```
dd if=/dev/zero of=/dev/hd_
``` 

Actually, you truly only need to overwrite the partition table with /dev/zero and not the whole disk. This provides enough protection for the vast majority of personal users. If you really want peace of mind though use a tool that's available on most linux systems called 'shred.'

---

### Post by stderr on 2009-01-04
> **Kinney said:**
> Just one question. I noticed that you are specifying a partition in the output. Would this work the same if I just used /dev/sdd since I've already deleted all of the partitions in fdisk?

Yes, you could do

```
dd if=/dev/zero of=/dev/sdX bs=1M
```
or, depending, 
```
dd if=/dev/zero of=/dev/hdX bs=1M
```

to overwrite an entire drive. Again, be very careful!

As these block devices appear to the system as files, you can write to them as above, and you can even read the contents of your drive from them. As an example, I accidentally overwrote a critical source code file that I'd spent a while writing, with a dumb compile command (something like this):

```
g++ -o ASourceFile.cpp AnotherSourceFile.cpp etc
```

Notice the -o (output) flag which is meant to specify the output file for the compiled binary, not-so-cleverly overwriting one of the source files. It should read something more like:

```
g++ -o MyApplication ASourceFile.cpp AnotherSourceFile.cpp etc
```

To retrieve the source file, I had to dump the entire contents of the partition through strings to a huge many-GB text file, and search through for the source code I'd deleted :) something like

```
strings /dev/sdc2 > /hugeTextFile
```

That too would have worked with a drive instead of a partition, such as

```
strings /dev/sdc > /hugeTextFile
```

Many other tools exist, as I and other posters have pointed out, for overwriting either once, or many times. It depends what you want to achieve and how paranoid about security you are. The good ol' 'Disk Destroyer' method is just one of those common, simple examples that always pops up - because, let's face it, every Linux box has dd already installed.

I used to use a variety of shredders, but in *reality*, a single pass over a file/device is almost bound to be sufficient for everything other than the most in-depth recovery attempts by experts. Or, to put it this way, one pass = pretty much impossible for normal people to retrieve, two passes = don't bother trying unless you've got special electromagnetic tools and stuff. The 'government' (DOD) verified wiping mechanism (I think it's a 7-pass procedure with different types of data at each stage) is only for the ultra-paranoid - and to go with that, it's ultra-slow ;)

@hundredwatt: The partition table would probably be sufficient in most cases, and it would be a lot quicker to simply wipe that. I don't think that would evade the 'strings /dev/sdX > afile' method though ;)

edit: You don't need to specify the blocksize with dd. If you don't bother with bs=1M, it will default to bs=512 (bytes). The reason I specify it is to speed up the copy. It's much much faster writing an entire drive in blocks of 1MB as opposed to blocks of half a KB

---

### Post by Feivel on 2009-01-04
How about introducing the HD to a magnet?

---

### Post by stderr on 2009-01-04
> **Feivel said:**
> How about introducing the HD to a magnet?

:D

I don't know if it would work correctly afterwards, and to get a large enough field applied (unless you have an incredible magnetic source) you'd probably have to disassemble the HDD to get close enough to the platters. Disassembly alone would get enough dust on them for it to be f***ed ;) 

So, yeah, if you don't want to use the drive afterwards, taking it apart is a great option. There are normally some pretty strong magnets in there anyway, for the drive motor if I recall. If you can remove the platters too... strong magnets... scratches... cuts... yeah, following a multi-pass overwrite of the drive, as they say, that'd be toast :p

---

### Post by Cracauer on 2009-01-04
> **Feivel said:**
> How about introducing the HD to a magnet?

No, you really need an oscillating field.

I tried magnets with a variety of magnetic data media and they were unimpressed. One magnet I used was from a JBL 120E, outside electromagnets it doesn't get much stronger.

Just wiping the disk once with zeros will not be totally safe. People with equipment that can work on an analog signal from the disks' head can probably restore past that. But I don't think you need safety against that, unless you have a problem with the KGB or something :)

---

### Post by Kain000 on 2009-01-04
bump Deirks boot and nuke!

I use it for each new drive I aquire piror to puting it into use.

on the other side does anyone know of a good recovery tool to use to dig arround a "wiped" drive?   I would love to see whats left on a few of old drives I have after the windows wipe.

---

### Post by ChildOfMana on 2009-01-05
For removing data [this]("http://ubuntuforums.org/showthread.php?t=861475&highlight=degauss&page=2") post may help - specifically the second page.

For recovering it, try [here]("http://ubuntuforums.org/showthread.php?t=417761").

---

### Post by masque7 on 2009-01-05
[http://www.dban.org/](http://www.dban.org/)
+1 for dban 

You can get a lot of applications to *completely* clean a drive, but dban should suite you just fine.

---

### Post by |{urse on 2009-01-08
> **Kain000 said:**
> bump Deirks boot and nuke!

I use it for each new drive I aquire piror to puting it into use.

on the other side does anyone know of a good recovery tool to use to dig arround a "wiped" drive?   I would love to see whats left on a few of old drives I have after the windows wipe.

yeah ^^ it's called "recuva" its a windoze program but works fine under wine too.

---

### Post by PCHome on 2009-01-22
The one I use is *Darik's Boot and Nuke* which is downloaded as a CD ISO file. It's not Ubuntu since that sort of thing should not be done when booted to another hard drive but rather DOS. Once burned, you boot to the CD and follow the prompts as to which drive and how many passes to make. It will wipe out the whole thing, which can take several hours for larger capacity drives. I prefer to be on the safe side by disconnecting any drives I don't want wiped! Don

---

