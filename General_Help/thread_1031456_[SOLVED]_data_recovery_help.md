---
title: "[SOLVED] data recovery help"
date: 2009-01-05
forum: General Help
---

### Post by NullHead on 2009-01-05
I did a backup of some files onto my server a few days ago, and when somebody else restored them for me, they "cut" and "pasted" them ... Is there any way to get those files that used to be on my server back? I've tried foremost, but that didn't find anything. Some of the files that got restored got accidentally removed from the computer that got the files. I've tried to restore then on the client side, but that didn't work. Restoring them from my server is the only hope left.  

Speculation is also appreciated.

---

### Post by NullHead on 2009-01-05
Bump.

---

### Post by lavinog on 2009-01-05
generally if you need to recover a file that was deleted you should first protect the drive from any write activity. ie: disconnect the drive and mount it to another system in read only mode. Once a file is deleted there is a possibility that the data will be overwritten by new data...that probability goes up when the available space goes down.
It also helps to know what types of files are you looking for.
e2undel
magicrescue
recover
are a couple of packages in synaptic that look like they may help
again when you recover the data, make sure it is saved onto a different partition/drive.

---

### Post by NullHead on 2009-01-05
Well see it's on my server which doesn't go under hardly any hdd activity. The hdd functions 100% and has a good filesystem. I'm about 70% sure the files will be recoverable, I just needed to know what programs to use ^_^

They're .dat files. To me, it seems like an easy retrieval, but I just don't know based on the fact that the files were cut and pasted onto a different computer through the network.

I'll give those programs a looking into. Thanks!

---

### Post by lavinog on 2009-01-05
> **NullHead said:**
> Well see it's on my server which doesn't go under hardly any hdd activity. The hdd functions 100% and has a good filesystem. I'm about 70% sure the files will be recoverable, I just needed to know what programs to use ^_^

It may seem like there is no activity, but there are log files that get written to on a regular basis...although not likely to overwrite your data, there is a potential for loss.
even installing one of the above programs could overwrite your data if your data existed on the same partition as the system
if the data was on a separate partition, then you shouldn't have much to worry about.

---

### Post by NullHead on 2009-01-06
Well I tested recover and it came up with nothing. I guess it's time to move on. As you said, logs logs logs, so I'm just going to forget about that data. Thanks anyways. 

Btw, all of the logs and things are on one single hard disk. So logs would've gotten written to the save device.

---

### Post by adult swim on 2009-01-06
before you give up you may want to try 
testdisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
photorec [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
photorec's wiki says it can recover .dat files

---

### Post by NullHead on 2009-01-06
Well I'm giving photorec a go. It estimates that it will take 5 hours to complete. I'm going to let it go over night and I'll share the results tomorrow. 

Thanks for the suggestion :D

---

### Post by NullHead on 2009-01-06
Well I'll just count the data as MIA ... I ran photorec, and it gave me about 600 directories full of deleted log files  ... all the directories were filled with txt files ... I opened a few, but they were useless. With the amount of data that got retrieved from the depths of the unknown, I'll just go ahead and say that the data is gone. 

Thanks for your help anyways :)

---

### Post by lavinog on 2009-01-06
> **NullHead said:**
> Well I tested recover and it came up with nothing. I guess it's time to move on. As you said, logs logs logs, so I'm just going to forget about that data. Thanks anyways. 

Btw, all of the logs and things are on one single hard disk. So logs would've gotten written to the save device.

what were the DAT files from?

---

### Post by NullHead on 2009-01-06
My little brother's math tutor software. His records were in those .dat files.

---

