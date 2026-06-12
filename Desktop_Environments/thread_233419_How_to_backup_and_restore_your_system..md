---
title: "How to backup and restore your system."
date: 2006-08-10
forum: Desktop Environments
---

### Post by Ausus on 2006-08-10
Hi All,

If you upgrade your Linux system and do repositories downloads.

1) How can you backup the easy way to safe all your new and down- loaded files.

2) How can you get back to your old linux system before the HD crash.

Is their a guide available, some where.

---

### Post by kaffelars on 2006-08-10
If I understand correctly, you want something like the Windows System Restore? 

I'm not aware of anything like this for Linux. Apple is implementing something similar in the next OS X, so I guess it's just a matter of time ;) 

If I'm wrong and that there already is something similar for Linux, I'd love to hear it!

---

### Post by Ausus on 2006-08-10
Hi kaffelars,

Yes partialy. What I'm trying to get accross.
Now you got your system 100% stable all application loaded.
Programs and from repositories.

What I saw under Alternate_AMD64 cd install that you could copy something??. Are these backups you made or what?.
Does anybody else have a answer.

How can I make a backup and restore that it is back to what I had it before when everything was 100%.

System restore under XP does not work 100%, it normaly screws up something.Then you have to do a complete restore anyway.
Regards

---

### Post by kaffelars on 2006-08-10
I know, it usually doesn't work when you really need it. But it's a great idea though, and I'm sure some brilliant open source programmers could make something similar, only better :) 

I'm sorry, but I don't understand the AMD64-question about copying something :sad:

---

### Post by ardchoille on 2006-08-10
There's an app in the repos called partimage. From the partimage homepage:

"Description: Partition Image is a Linux/UNIX utility which saves partitions in many formats (see below) to an image file. The image file can be compressed in the GZIP/BZIP2 formats to save disk space, and split into multiple files to be copied on removable floppies (ZIP for example), ... Partitions can be saved across the network since version 0.6.0."

I have been using partimage and I quite like it. I have a copy of System Rescue CD ([http://sysresccd.org](http://sysresccd.org)) and this cd makes using partimage very easy.

Basically, what partimage does, is it takes the **used** space on a partition and save it to an image file (compression is available). You can burn that image file to CD/DVD and use it to install Linux to several machines or keep it as a backup in case of a catastrophe.

---

### Post by FeestBijtje on 2006-08-10
Install automatix and then install trough automatix tha backup and restore tool here is the link to the automatix threadt.
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

### Post by kaffelars on 2006-08-10
Correct me if I'm wrong, but I believe partimage and the backup/restore software installed by Automatix are to very different solutions.

Partimage creates complete images of a drive, while the other only backs up selected files and folders.

I'm not sure which one is closest to a "system backup and restore"-application though..

---

### Post by ardchoille on 2006-08-10
> **kaffelars said:**
> Correct me if I'm wrong, but I believe partimage and the backup/restore software installed by Automatix are to very different solutions.

Partimage creates complete images of a drive, while the other only backs up selected files and folders.

I'm not sure which one is closest to a "system backup and restore"-application though..

Partimage backs up partitions, not drives. I use it to back up my / partition and burn the image to cd. If I ever have a major problem with my root partition, I simply restore from the image partimage created and the root partition is back to the way it was before the problem occurred.

And, read some of the automatix forum posts before you use automatix.

---

### Post by Ausus on 2006-08-10
Hi kaffelars,

When using this ubuntu-6.06-alternate-amd64.iso file and make a working cd from this. When you do the install you have option Text;OEM and others.

 During the Text option installation you have a option to copy something?. I cant remember the detail what is asked about it.

I also cant take a screen shot of this, because it is busy installing Ubuntu.

Regards

---

### Post by kaffelars on 2006-08-10
To be honest, I don't know.
I have only installed Dapper once, and that was a beta version of the desktop CD.

---

