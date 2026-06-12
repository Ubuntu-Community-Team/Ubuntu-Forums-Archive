---
title: "I made a mistake remounting drives, Have I lost all my data?"
date: 2009-02-21
forum: General Help
---

### Post by grs on 2009-02-21
I have a 500GB HDD which had some files on it, I was reinstalling my storage server and rather than going to fstab and just adding the HDD back in there I accidentally tryped in the mkfs command, this has wiped all the data from the drive.

Is there any way of retrieving the data or is it all gone for good?

I add drives of infrequently that I forget the process!!

---

### Post by taurus on 2009-02-21
Maybe TestDisk can do something about it, [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).

---

### Post by cariboo on 2009-02-21
You may be able to resuce your lost data using [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"). Testdisk is available in the repositories.

Jim

---

### Post by grs on 2009-02-21
I'll have a look at test disk then. The problem is not on my Ubuntu PC, it's on a Red Hat based server called Clarkconnect. I suppose it will run much the same. Can't seem to find a Testdisk specific forum.

I've just tried to install it with the following command but it doesn't seem to be working.

```

apt-get install build-essential e2fslibs-dev libncurses5-dev libncursesw5-dev libntfs-dev libjpeg62-dev libreiserfs0.3-dev uuid-dev zlib1g-dev

```

---

### Post by cariboo on 2009-02-21
Apt-get will not work on a Red Hat based computer,  Red Hat uses rpms. It has been about 10 years since I vowed never to use an rpm based distro again,  so I  won't be much help.

You could try [Ubuntu Resuce Remix]("http:///ubuntu-rescue-remix.org/Download"), as testdisk is included.

Jim

---

### Post by Irihapeti on 2009-02-21
You can get Testdisk as part of several live CDs such as Parted Magic, GParted, System Rescue CD and so on. There's also this: [http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/) OK, it's written for Windows users, but the principles are the same. Another useful link is [http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by grs on 2009-02-21
I'll have a closer look at the live cd options, thanks for the advice.

---

### Post by grs on 2009-02-28
> **Irihapeti said:**
> You can get Testdisk as part of several live CDs such as Parted Magic, GParted, System Rescue CD and so on. There's also this: [http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/) OK, it's written for Windows users, but the principles are the same. Another useful link is [http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

I'm trying testdisk based on the guide from your first link, but it doesn't seem to be running right. It starts scanning saying it will take X amount hours and after a few seconds an error comes up about a segment error , I think that was it, the PC froze and I had to restart it. Any ideas?
I can run it again and get the exact wording.

---

### Post by Irihapeti on 2009-03-01
I have to admit I've never actually used Testdisk myself, so I can't be of a great deal of help, unfortunately. By that, I mean that I've played with it to see what it can find on a healthy drive, but not to recover something I've accidentally deleted. 

There seem to be a number of useful-looking references on the second link in my earlier message. Other than that, all I can think of at this stage is asking on one of the recovery software forums.

---

### Post by caljohnsmith on 2009-03-02
I would recommend trying the latest 6.10 stable version of testdisk; to use that version, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop (can be your Ubuntu install or a Live CD), and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions you think might be the ones you want to recover. We can work from there if you want.

---

### Post by grs on 2009-03-02
I'll give that a go. I'm running it from the Live CD. The drive I'm trying to salvage data from was originally formatted to EXT3.

Here are the results


```

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1 60800 254 63  976768002




Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock, 500 GB / 465 GiB

```

---

### Post by grs on 2009-03-04
Does this read out mean anything? what should I do next?

---

### Post by Irihapeti on 2009-03-04
grs:

To me, it looks as though your partition is recoverable. 

However, if you wanted to be certain, I would suggest waiting a little longer to see what caljohnsmith has to say. He once helped me out of a tricky situation, and I think he knows a good deal more about this than I do.

Or maybe someone else who has actually resuscitated a formatted drive may be able to advise.

---

