---
title: "Trying to mount windows HDD: Access denied"
date: 2008-12-11
forum: General Help
---

### Post by iamfromhuntersbar on 2008-12-11
Hello everyone!

So, I'm a complete beginner when it comes to Linux and Ubuntu, so be gentle with me and sorry for all my stupidity in advance!

Here's my story;

I've got a Sony Vaio laptop with 2 HDD mounted in a raid (100GB each), I got a nasty virus and now I'm in a BSOD/restart loop which is really getting to me!

I've used Ubuntu AGES back to restore a HDD, so I thought I'd give it a crack again!

Anyway, what I'd like to do is mount my two drives (C: and D:) and transfer all the files I want to keep from C: to D: before I wipe C: and re-install windows onto it.

But I'm stuck before I've even started guys ... help me!!

Oh, and I'm running Ubuntu straight off the CD!

Many, MANY thanks in advance!

J

---

### Post by used2bnewb on 2008-12-11
What do you mean by access denied?

Have you tried sudo?

```
sudo mount sda
```Please replace the a in sda with your drive letter

---

### Post by iamfromhuntersbar on 2008-12-11
I try that (no matter the letter) I get;
mount: can't find sda in /etc/fstab or /etc/mtab

---

### Post by Locke_99GS on 2008-12-11
The drive is not showing up in gnome's Places menu? The LiveCD should automatically detect all of your partitions.

---

### Post by iamfromhuntersbar on 2008-12-11
Nope, I'm afraid not, and it's not showing up in 'File System' either!

---

### Post by Coreigh on 2008-12-11
First off you need to specify the partition number. If C: is the first partition on the disk then:
```
sudo mount /dev/sda1 /media/disk
```

Use the output of "sudo fdisk -l" to determine partitions and disk order.

Second you may have difficulty mounting the Windows file system (NTFS) because it was not cleanly un-mounted on last use. You may have to force the mount. Bear in mind this adds further risk to the data, but that's what last resort options do.

---

### Post by Thura on 2008-12-11
First find or make an empty folder ... 
Then use 

sudo mount /dev/sda /path/to/your/folder

I am assuming the drive you want to mount is /dev/sda
You can easily know what is your drive by `sudo fdisk -l`

```

thura tmp :sudo fdisk -l
[sudo] password for thura: 
Sorry, try again.
[sudo] password for thura: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   5  Extended
/dev/sda2            5223        7833    20972857+   7  HPFS/NTFS
/dev/sda4            7834       14593    54299700    7  HPFS/NTFS
/dev/sda5               1        3824    30716217   83  Linux
/dev/sda6            3825        3947      987966   82  Linux swap / Solaris
/dev/sda7            3948        5222    10241406   83  Linux

```


For e.g,
For my machine, I use 
```
thura ~ :sudo mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
thura ~ :mkdir tmp
thura ~ :sudo mount /dev/sda2 tmp/
thura ~ :sudo umount tmp/
```

After transferring your data to another drive, you need to umount it to wipe ( format ) it ..

---

### Post by iamfromhuntersbar on 2008-12-11
OK, so if I type the sudo fdisk -l I get;
"Unable to seek on /dev/sda"

and when I try sudo mount /dev/sda2 tmp/ I get;
"Mount point tmp/ does not exist"

---

### Post by Thura on 2008-12-11
>> and when I try sudo mount /dev/sda2 tmp/ I get;
 >> "Mount point tmp/ does not exist"
As I noted, You need to make sure there is a folder named "tmp" in current working directory to use "sudo mount /dev/sda2 tmp/"
In my example , I use "**mkdir tmp**" to make a new folder ... ( You missed it ? )

Still, you cannot type **/dev/sda2** , this will only work for me ( my computer )
You need to get your drive name ...

Why fdisk -l is not working ???
Can you use System >> Administration >> Partion Editor ( just to check your drive )
or try this ...
```

ls -al /dev/ | grep sda

```

---

### Post by iamfromhuntersbar on 2008-12-11
Partition editor shows that I have two devs, 
/dev/sda (93.16GB) and /dev/sdb (93.16GB)

fdisk is just saying that it can't seek sda!

Ooh, we may be getting somewhere here (or not!)
When I make my new folder (mkdir jbs) then try and mount them to it I get;
"Mount: unknown filesystem type 'lsw_raid_member'"

---

### Post by Thura on 2008-12-11
What is your drive C partition type  ? ntfs fat ?
Then you can manully set type by  " -t "
```

thura ~ :sudo mount /dev/sda2 -t ntfs /media/cdrom0/
```

---

### Post by iamfromhuntersbar on 2008-12-11
I'm pretty sure it's NTFS (it's XP after all), but I think it's configured in a raid across the 2 discs ... that may be where my biggest problem lies.

---

### Post by Thura on 2008-12-11
Then try with the " -t ntfs "
If it doesn't work, sorry I don't have any other ideas .. ;(
Good Luck !

---

### Post by nzadLithium on 2008-12-11
What I think you need plugged into your pc in the way of drives, is cd/dvd drive (for livecd), drive to store recovered files on and **ALL** the disks that were participating in raid in the old hardware setup setup in raid on this pc. 

I'm not an expert in raid by any account, but from what i've heard about it, it 'joins' the disks together, as one large disk. Therefore the filesystem will be created over the two (or more) disks, so if you attempt to recover data from only one disk, it would be missing half the filesystem.

---

### Post by fjgaude on 2008-12-11
> **iamfromhuntersbar said:**
> I'm pretty sure it's NTFS (it's XP after all), but I think it's configured in a raid across the 2 discs ... that may be where my biggest problem lies.

The only way to see a Windows, BIOS raid is through the use of a program called **dmraid**, which is in the repository. Download it and then read the **man** pages for it.

---

### Post by iamfromhuntersbar on 2008-12-12
Ah right, I thought as much! How do I go about downloading and installing that from live then!?

---

### Post by iamfromhuntersbar on 2008-12-12
OK, I've got dmraid installed ... and it recognises my 2 HDDs I think ... but I still can't mount them! Booo!

---

### Post by iamfromhuntersbar on 2008-12-12
OK, so I've got it sorted! Woohoo!

Thanks for all your help guys! I had to force mount my drives in the end, but dmraid was the winner for me!

---

### Post by fjgaude on 2008-12-13
Great, glad that **dmraid** came through for you... /mapper/... does the trick with mounting and putting a line to auto mount in your **fstab** file.

---

