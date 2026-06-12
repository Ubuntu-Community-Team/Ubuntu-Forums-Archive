---
title: "Recovering a formatted hard drive?"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Joseph Elliott on 2006-07-19
Im not sure where to put this but can anyone tell me how i can recover files from a harddrive that has had its partions deleted/refomatted twice?  i want to recover my pictures from my documents (its a windows system).  is it even possible? ](*,)

---

### Post by dtfinch on 2006-07-19
In a quick minute of searching, I noticed a program for reading a volume and extracting all the jpegs:
[http://www.suse.de/~thomas/projects/jpeg-extract/](http://www.suse.de/~thomas/projects/jpeg-extract/)

I suppose you'd just hook up the drive as a slave in another system and run jpeg extractor on /dev/hdb or whatever. It's likely to be slow, reading one byte at a time. It's meant for small flash drives. I haven't tried it myself.

It's likely to have some difficulty with very large images though, because the jpeg end of file marker is only two bytes long, and likely to appear in the data of images larger than 64k.

Edit: It looks like it'll catch a lot of false positives, because it only uses 2 bytes to identify the beginning.
Edit 2: Another jpeg extractor written in Java. Checks first 3 bytes, for fewer false positives. [http://schmidt.devlib.org/software/jpeg-extractor.html](http://schmidt.devlib.org/software/jpeg-extractor.html)

In the unlikely event that all you've done is repartition, without reformatting, a full recovery might be possible. Just repartition to exactly the way it was before.

---

### Post by tturrisi on 2006-07-19
if have access to a windows comp use this FREE app:
[http://www.pcinspector.de/file_recovery/UK/welcome.htm](http://www.pcinspector.de/file_recovery/UK/welcome.htm)
works very well as does its counterpart PC INSPECTOR™ smart recovery

---

### Post by bigken on 2006-07-19
the best program I have used for this has being ontrack data recovery software I have  had quite a high sucsess rate using it only thing this is not a free software package ;)

---

### Post by az on 2006-07-19
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Foremost works great.

You will need to have a hard drive onto which you will dump your data.  Boot the live cd, download and compile the latest versino of foremost, mount your data drive somewhere (/mnt) and do

sudo foremost -i /dev/hda1 -o /mnt

where hda1 is the partition where your stuff used to be.


If you have not overwritten your data, you will be fine.

---

### Post by T700 on 2006-07-19
> **Joseph Elliott said:**
> Im not sure where to put this but can anyone tell me how i can recover files from a harddrive that has had its partions deleted/refomatted twice?  i want to recover my pictures from my documents (its a windows system).  is it even possible? ](*,)

It's been formatted twice?  Was anything (like an installation of an OS) written to it after either of those formats?  My guess is, your data is gone.

Paul

---

### Post by Joseph Elliott on 2006-07-20
No Operation system was written overtop however i used a program that came with the hard drive to change the partition.  thanks for the advice i greatly appreciate it

---

### Post by az on 2006-07-20
> **Joseph Elliott said:**
> No Operation system was written overtop however i used a program that came with the hard drive to change the partition.  thanks for the advice i greatly appreciate it

If you mean that you just changed the properties of the partition, your data is still there.

You can even use parted to find the lost partition and add it back to the partition table.  It will be as if it never was gone.


Editing the partition table is not formatting.  And even after you format, you can recover data.

---

### Post by clint1010 on 2006-07-20
I have had great success with "Get Data Back" in the past, even on a formated drive, (data was not overwritten), but this is not free software

---

### Post by Joseph Elliott on 2006-07-21
umm azz how do i compile that program, im still trying to figure everything out with a linux system and im having a hard time converting from windows.  it doesnt help that i have no knowledge of such things to begin with :-k  and thanks to everyone who took the time to help.

---

