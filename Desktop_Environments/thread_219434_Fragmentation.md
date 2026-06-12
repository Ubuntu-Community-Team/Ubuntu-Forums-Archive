---
title: "Fragmentation?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Sunnz on 2006-07-20
> Fragmentation occurs when a file tries to fit into a gap on the hard disk that is too small for it. Say you delete a 10Kb file, which leaves a gap free on the hard disk. Then you try and write a 15Kb file. Only the first 10Kb can fit where the old file went. The rest has to go elsewhere on the disk, thus fragmenting the file.

Fragmentation will require that the head jump from one part of the disk to another in order to complete the file reading. If the head has to move around the hard disk hither and thither, a lot of time is going to be wasted (this is why access times are so important). For this reason, defragging your disk periodically is important. Defragging will attempt to re-align files so that the entire file can be found in one place. In Windows XP, the defragger can be found under Start-Programs-Accessories-System Tools. 


Ok, I have been using Linux for ages and haven't done any defrag... and I almost never heard people do it on Linux... but maybe I missed out something? I used to do it all the time in Windows on FAT32...

I guess my question is, is it necessary to defrag on Linux, in genernal? If it is not necessary, why?

P.S. Using reiserfs, btw.

---

### Post by aysiu on 2006-07-20
[http://en.wikipedia.org/wiki/Reiserfs#Criticism](http://en.wikipedia.org/wiki/Reiserfs#Criticism)

---

### Post by Thenotsowyzewun on 2006-07-20
Defragging hasn't really been necessary since Windows 2000 - Windows ME and all the OS's before it from Microsoft used FAT32, which was really really terribly designed!
People have carried on defragging tho with the new NTFS filesystem on 2000, XP etc 'cos they're used to doing it.

You can defrag Linux's Ext3 filesystem, and it will bring a slight performance increase, but to slight to be physically noticeable.

Linux doesn't get fragmented, how cool is that!

---

### Post by FredB on 2006-07-20
I disagree. NTFS is fragmenting too. I used 2000 and XP and after a week, without defragging, you'll see a decrease of speed.

Ext3fs and other linux based system are built for avoiding fragmentation. Also, linux is only the heart, not the whole distribution :p

---

### Post by Sunnz on 2006-07-20
Well after some readings from wiki, it seems like all file systems will have some sort of fragmentation, only to what extend that matters.

So is it that there is no known algorithms to store bits such that there is no fragmentation?

It seems like XFS is the best from what I have seen, has the least fragmentation and has tools to defrag... but it is not very popular at all, anyone know what's its downside?

---

### Post by blueturtl on 2006-07-20
> Fragmentation occurs when a file tries to fit into a gap on the hard disk that is too small for it. Say you delete a 10Kb file, which leaves a gap free on the hard disk. Then you try and write a 15Kb file. Only the first 10Kb can fit where the old file went. The rest has to go elsewhere on the disk, thus fragmenting the file.

Fragmentation will require that the head jump from one part of the disk to another in order to complete the file reading. If the head has to move around the hard disk hither and thither, a lot of time is going to be wasted (this is why access times are so important). For this reason, defragging your disk periodically is important. Defragging will attempt to re-align files so that the entire file can be found in one place. In Windows XP, the defragger can be found under Start-Programs-Accessories-System Tools.
[QUOTE]I guess my question is, is it necessary to defrag on Linux, in genernal? If it is not necessary, why?[/QUOTE]

You don't usually have to defragment under Ubuntu, unless your hard-disk becomes full. As far as I know (and I'm not an expert) Ubuntu and other Linux distributions do smarter placement of files (aka. they will try to automatically fit the new files into a free segment on the disk that is large enough to contain the file completely). If your hard-disk becomes very full, it is no longer possible to do this, and then you will get more fragmentation.

---

