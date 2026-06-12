---
title: "how to recover ntfs partition after format to reiserfs"
date: 2007-06-19
forum: Desktop Environments
---

### Post by lacoona on 2007-06-19
Hi all,
Here's my problem:
I started installing kubuntu Feisty, and at the partitioning phase something messed up. I already had prepared a root partition and a home partition, but forgot about the swap partition. As I had a 130 gb ntfs partition, I wanted to take 512 mb for swap partition. This operation ended up with an error and now my 130 gb partition appears as a reiserfs partition and it is empty. The whole thing happened very fast, I imagine that only quickformat has been done on it. The 512 mb partition has not been created. 
As I did not mark the drive to be converted and formatted, I don't know how could this happen.
I installed Feisty without the swap partition.
Since then nothing has been written to this partition. What are my chances to recover my data from the ntfs partition? and how can I do this?
I could use ntfs tools only if I would convert it back to ntfs, but this operation would mess up even more the partition in my opinion, but maybe I'm wrong.
If some of you guys had such a problem and managed to solve it, please give me some hints.
Thanks.

---

### Post by scannerdarkly on 2007-06-19
I can't think of any tools under Linux for this but what it sounds like to me you need to say bye bye to your data.  When it comes to data recovery like that you won't be able to recover everything.  Once the drive has been format it the only way to change it back is to reformat it back.  but that will give you less of a chance for you to recover your files.  We all make mistakes and I've done what you did before, not a big deal.

---

### Post by lacoona on 2007-06-19
The thing is I don't know what went wrong, I did NOT say to parted to convert or format the drive. 
if I'm the guilty one, I don't know what was my mistake, this way I can't learn from it. If some software error is responsible for this, that's quite unfortunate, because it can happen to other people too.
If I would have had not too relevant data on it, I would not make a big deal of it, but I would really need the data... (for not backing up the data I'm guilty 150%, that's for sure, but this won't help me in this situation at all)

---

### Post by Sloddy Shipper on 2007-06-19
Hi, i'm not any kind of file system expert but i would be more optimistic about recovering your data here if only a quick format has been performed. I expect someone can tell you whether manually editing the partition table is likely to make things worse or if you could successfully recreate the NTFS partition in this way. I wouldn't like to offer any advice here other than don't give up yet.

Also if you still have a windows installation you can use and a bunch of extra disk space on another partition i have had success in retrieving files from formatted disks using this program -

 
[http://www.theabsolute.net/sware/dskinv.html]("http://www.theabsolute.net/sware/dskinv.html")

It can be a bit tricky to use and you MUST save any data you recover to another disk or partition otherwise you may overwrite as yet unrecovered data. Good luck.

---

### Post by Sloddy Shipper on 2007-06-19
Also, just found this which looks even more useful for your situation though i've never used it - 

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Hope this helps you, i'm going to give it a go on my knackered XP disk.

This is in a repository, so you can install via synaptic or apt-get

---

### Post by wirelessmonkey on 2007-06-19
EasyRecovery Professional can probably get your data back, but it's windows native.... I've been able to recover reformatted and rewritten partitions, even whole drives, but you'll have to find a copy somewhere. They may have a demo. [http://www.ontrack.com/easyrecoveryprofessional/](http://www.ontrack.com/easyrecoveryprofessional/)

---

### Post by lacoona on 2007-06-19
> **Sloddy Shipper said:**
> Also, just found this which looks even more useful for your situation though i've never used it - 

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Hope this helps you, i'm going to give it a go on my knackered XP disk.

This is in a repository, so you can install via synaptic or apt-get

Thanks for the tip Sloddy Shipper! I already downloaded the ubcd iso but did not have time to try it. It contains the Testdisk utility and the I tried to search for lost partitions, and it found my partition, but with the message: the partition can't be recovered. :((
I'm not giving up this easy, already downloaded some other utilities.

---

### Post by romper on 2007-12-22
Hi,

I reckon this is maybe a bit late to respond this message, but maybe other users can use it. I've had the same problem with my ntfs partitions. Ubuntu didn't recognise any of my partitions and I used dmraid so they would be recognised. All went well until I tried to create a new reiserfs partition for Ubuntu with Gparted. Somehow Gparted used the whole disk for the reiserfs partition. The good thing was, I didn't write anything on the disk! But it was format to reiserfs.

So what I did was used a proprietary program called partition table doctor 3.5 [http://www.ptdd.com/](http://www.ptdd.com/) (You will need the full version not the demo!). It is based on freedos so I could use the bootable image they provided. When the image has booted click "rebuild partition table". All partitions were correctly found! After that click on the bootable partition and click fixboot.

Now all NTFS partitions were back, but the data still not readable. So I started the Windows repair environment from the installation cd. Then type "chkdsk /r". Chkdsk will look for readable data and try to recover it. And it did. After this I repaired the old install with Windows install disc. This was necessary because I think I tempered with the old installation when testing some other options, so I don't know wether the re-install part is mandatory, but it worked for me. 

The partition table doctor was very simple to use and worked quite fast, but there surely are much more programs that can do the same or even better and are free in use. If someone knows of a program that can do the same and is usable with the Ubuntu live environment, then please post it here.

Hope this helps you out.

---

### Post by Wiebelhaus on 2007-12-22
> **romper said:**
> Hi,

I reckon this is maybe a bit late to respond this message, but maybe other users can use it. I've had the same problem with my ntfs partitions. Ubuntu didn't recognise any of my partitions and I used dmraid so they would be recognised. All went well until I tried to create a new reiserfs partition for Ubuntu with Gparted. Somehow Gparted used the whole disk for the reiserfs partition. The good thing was, I didn't write anything on the disk! But it was format to reiserfs.

So what I did was used a proprietary program called partition table doctor 3.5 [http://www.ptdd.com/](http://www.ptdd.com/) (You will need the full version not the demo!). It is based on freedos so I could use the bootable image they provided. When the image has booted click "rebuild partition table". All partitions were correctly found! After that click on the bootable partition and click fixboot.

Now all NTFS partitions were back, but the data still not readable. So I started the Windows repair environment from the installation cd. Then type "chkdsk /r". Chkdsk will look for readable data and try to recover it. And it did. After this I repaired the old install with Windows install disc. This was necessary because I think I tempered with the old installation when testing some other options, so I don't know wether the re-install part is mandatory, but it worked for me. 

The partition table doctor was very simple to use and worked quite fast, but there surely are much more programs that can do the same or even better and are free in use. If someone knows of a program that can do the same and is usable with the Ubuntu live environment, then please post it here.

Hope this helps you out.

yea , I've seen that , supposed to be top notch , I think the Helix forensics disc has it or something similar.

---

