---
title: "External hdd issues"
date: 2010-10-14
forum: Desktop Environments
---

### Post by peter_parker on 2010-10-14
Hey guys,
 
i'm trying to make my external hard drive read write. How would i go about doing this?
 
i'm using the command:
 
sudo mount /dev/sdb1 /media/mynewdrive
 
where do i stick the -rw switch?

---

### Post by mikewhatever on 2010-10-14
You shouldn't need to, since rw is a default option for mount.
Anyway, what you want is something like this:

sudo mount -o wr /dev/sdb1 /media/mynewdrive

---

### Post by peter_parker on 2010-10-14
alright.  so when i use:


sudo mount -o wr /dev/sdc /home/username/Desktop/External_HDD

It gives me:

mount: you must specify the filesystem type


I can successfully mount the drive with:

sudo mount -t hfsplus /dev/sdc /home/username/Desktop/External_HDD

(i forgot to mention that this hard drive is formated as hfsplus..sorry)

any ideas?

---

### Post by mikewhatever on 2010-10-15
Ideas about what? I mean, you know how to specify the file system and how to pass the rw argument.

sudo mount -t hfsplus -o rw /dev/sdc /home/username/Desktop/External_HDD

---

### Post by nothingspecial on 2010-10-15
I have never used a mac or hfsplus drive in my life, but I believe you have to disable journaling in order to mount it rw on a linux system.

---

### Post by coffeecat on 2010-10-15
> **nothingspecial said:**
> I have never used a mac or hfsplus drive in my life, but I believe you have to disable journaling in order to mount it rw on a linux system.

As a Mac user who has frequently used hfs+ to transfer files between my Mac Mini and my Ubuntu machine, I can tell you quite categorically, nothingspecial, that you can now suspend your belief and replace it with certainty. :)

@peter_parker, you need to do one of three things:

1 Reformat the drive as hfs+ non-journalled - that's "Mac OS Extended" without anything in brackets in MacOS's Disk Utility. I thought there was an easy way of enabling/disabling the journal in hfs+ but I can't find it in Disk Utility. I'll post again if I find anything.

2 Use FAT32.

3 Install the NTFS-3g driver in MacOS for read-write and use NTFS. Not a good idea if you don't have Windows to repair the NTFS filesystem if need be.

**Edit**: OK - posting from MacOS. This is how you enable/disable journalling in hfs+ in MacOS.

Enable - Open Disk Utility and highlight the hfs+ mounted partition. From the Disk Utility menu: File > Enable Journalling.

Disable - Requires the use of the terminal. :-s Open a terminal and:

```
diskutil disableJournal /Volumes/VolumeName
```If you're not sure of VolumeName, 'ls /Volumes/' in the terminal will reveal it.

---

### Post by peter_parker on 2010-10-15
I can't really reformat my hard drive, because currently i have no where to dump my data...
 
I have my old Mac, that's on its last leg, but should be ok enough for me to just disable jounaling on my hdd.
 
Then i'll try to mount it on my Ubuntu system, with:
 
sudo mount -t hfsplus -o rw /dev/sdc /home/username/Desktop/External_HDD

Hopefully that works.
 
Thanks guys!!

---

### Post by coffeecat on 2010-10-15
> **peter_parker said:**
> Then i'll try to mount it on my Ubuntu system, with:
 
sudo mount -t hfsplus -o rw /dev/sdc /home/username/Desktop/External_HDD

You don't have to. If you simply plug it in, it will get automounted. And if you have disabled the journal it will be autmounted read-write.

But you will still have one problem. If you try to write to the drive by drag and drop to the root of the filesystem (or any folder you don't own in Ubuntu) you will get a permissions denied error. This is because hfs+ supports the same Unix permissions that both Linux and MacOS use and the root of the filesystem will be owned by - er - root. You'll need to do some 'sudo chown'-ing. Post back if you need help with that.

If you are simply copying off the drive by drag and drop you may or may not get permissions errors depending on what rwx permissions MacOS gave to the files.

---

### Post by peter_parker on 2010-10-18
so. i believe i disabled journaling and tried mounting to my linux system.

ran the command:  chown -R inawaz:inawaz /home/username/Desktop/External_HDD

but no luck.  when i try to drag a file into the external hdd i get a 'the destination is read only' error...

i mount it with sudo mount -t hfsplus -o rw /dev/sdc /home/username/Desktop/External_HDD

any help?  thanks

---

### Post by coffeecat on 2010-10-19
> **peter_parker said:**
> so. i believe i disabled journaling and tried mounting to my linux system.

ran the command:  chown -R inawaz:inawaz /home/username/Desktop/External_HDD

but no luck.  when i try to drag a file into the external hdd i get a 'the destination is read only' error...

i mount it with sudo mount -t hfsplus -o rw /dev/sdc /home/username/Desktop/External_HDD

any help?  thanks

Are you sure it wasn't automounted? There's something wrong if it wasn't automounted to a dynamic mountpoint in /media.

If it wasn't automounted to somewhere in /media, then when you did a 'sudo mount' to ~/Desktop/External_HDD the filesystem will still be owned by root. Which means that when you 'chown -R inawaz:inawaz....' you get a permission denied error. Correct? You have to use sudo, as in:

```
sudo chown inawaz:inawaz /home/username/Desktop/External_HDD
```Note that I have omitted the -R option. By omitting -R you will 'own' the root of the filesystem, which will be enough to copy files there and/or to make new folders. Use the -R option only if you need to recursively own all the folders and files already there. Depending on the permissions set by MacOS when it originally wrote the files you may or may not have to do this. If you do, you may encounter permissions problems when using that drive on your Mac. The reason is a differing UID between your Mac and Ubuntu. Both MacOS and Ubuntu use Unix permissions, but your UID (user identity number) in Ubuntu will be 1000, but in MacOS it will be 501 (iirc).

If it was automounted to /media/whatever, then you simply need to do the same, sudo chown /media/whatever. Before you do any chown-ing, check that the drive is not automounted. Mounting to two mountpoints is not a good idea.

---

