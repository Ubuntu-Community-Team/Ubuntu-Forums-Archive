---
title: "[SOLVED] (8.10) Cannot mount volume"
date: 2008-12-03
forum: General Help
---

### Post by thelugnut on 2008-12-03
I do not understand "mounting". 
I have one hard disk. See screen shot of gparted partitions.
When I attempt to open the sda-5 partition, I get a dialog box, see screen shot sda-5 partition (2).
I also enclosed a couple of screen shots showing the "properties" of sda-1 and sda-5. They are not the same. I don't understand that either.
I guess I need some basics here, since it is all muddy for me.:confused:

---

### Post by DagMan on 2008-12-03
What is on sda3?  Is it files that are usually part of the operating system... like is it meant to be mounted at /var or /usr or some other location or somewhere in /media ?

How are you trying to mount it?  At the command line, through fstab, or both, and can you post the relevant command you're using to mount it in either case, either the fstab entry or the terminal command or both?

---

### Post by wylfing on 2008-12-03
Hmmm, something does not add up here. Who did this disk partitioning for you?

The Ubuntu Wiki article on mounting may give you just enough information to be dangerous, but I'll link it here anyway: [https://help.ubuntu.com/community/Mount]("https://help.ubuntu.com/community/Mount")

Essentially, mounting is how volumes are accessed in Windows via drive letters, except in the Unix world (including Linux) you can attach volumes to any part of the directory structure and they don't have letters assigned to them. It's called mounting in Windows-land too, but effort is taken to hide this from Windows users.

---

### Post by thelugnut on 2008-12-03
The message appears when I click on the sda5 icon. That is : Places> Computer> 94.4 GB Media. This is when I get the first message. I usually just click on O.K. and the section opens and I can access it.

The files on sda5 are data files. 

I partitioned the hard disk this way, because I have Windows XP on the sda-1 partition, Ubuntu 8.10 on the sda2 partition and data stuff on sda5 partition. Both Windows XP and Ubuntu can read the data files. It makes things convenient for me.

I was investigating (means playing with) the PING program. I backed up the Windows partition, sda1 on partition sda5. That worked all right, but now when I try to restore it, the PING program tells me it can not "mount that partition. That's where I am at now.

---

### Post by wylfing on 2008-12-03
I could tell from your partition layout what your basic strategy was with dual-booting and a data partition. The reason I said something does not look right is that sda3 looks like a bunch of wasted space.

Anyway, in order to access sda5 you may need to explicitly mount it, and/or create an entry for it in /etc/fstab. For example:
```
sudo mount -t vfat /dev/sda5 /media/shared_data
```
Where "/media/shared_data" is wherever you want to mount sda5 in your system (the directory needs to exist). Then try navigating to that directory and see if you have access to your stuff.

I am not terribly familiar with PING, so I can't provide any guidance on using that.

---

### Post by thelugnut on 2008-12-07
Excuse me for the late reply...such is life in the fast lane.

Thanks for the input. I will try it and see, but it won't be for a few days, I think..

Again, thanks for answering.

---

### Post by thelugnut on 2008-12-08
I tell you, I must be thick as mud. I just don't seem to be able to catch on. I read the thirtyfive pages of Man -Mount and got even more confused.
Can you explain it as if you were explaining to a five year old? I mean step by step? I haven't had this much trouble picking up on something since my daddy told me about the birds and the bees.:confused:

---

### Post by wylfing on 2008-12-08
OK - your disk has 5 partitions on it. When you boot into Windows, you probably see drives C, D, and G. (The letter of the last one might be different but it doesn't matter.) What Windows has done for you is to look at your disk, identify all the partitions it can make sense of, and *mount* them into the filesystem.

The idea of mounting is that there is some point of access, where the user can get access to the data on those partitions. The way Windows shows this to the user is with "drive letters" (for very bad historical reasons). Drive letters are what you would call the "root" of the Windows file system - a drive letter is the shortest possible path you can type.

On Linux (and all other Unix-like operating systems, including Mac OSX), there is a "root" that has nothing to do with disks. It just exists. The root of the file system is called "/" and you can see /dev/sda2 is mounted on "/", which means that the top of the file system on the sda2 partition has been welded onto the top of the "real" file system.

You might think that / is therefore equivalent to C: but this is untrue. The sda2 partition didn't have to be mounted at /. It could have been mounted anywhere in the "real" file system. The top of sda2 could be at /home or /mnt/disks/sharkie or wherever you wanted it to be. Now you won't get very far without a bootable partition mounted on /, so sda2 is fine where it is :p but the lesson is that it could have been mounted anywhere else.

It's the same with other devices - they get mounted into the filesystem at various places. When you pop a disc into your optical drive it is mounted at /media/cdrom. (Try it and see!) Everything has to be mounted into the filesystem for it be accessible, and in Linux those "mount points" can be just about anywhere.

For your specific problem, I am guessing that sda5 isn't being mounted. You tell your computer you want to browse this thing, and it looks at this large fixed disk and knows you probably want to mount it but it has no idea *where* you want to mount it or what your purpose is for mounting it, etc. So it throws up its hands in confusion. My suggestion is to tell it exactly what you want to do - give explicit commands about what's on the partition and where you'd like it to be mounted in the file system. That's where the 'mount' command comes in.
```
sudo mount -t vfat /dev/sda5 /mnt/shared_disk
```
The 'mount' command you recognize. 'sudo' is to elevate your priveleges because mounting new things into the file system is a priveleged operation. The 't -vfat' portion identifies the partition as a FAT32 file system. '/dev/sda5' is the name of the partition you want to mount, and '/mnt/shared_disk' is the location in the file system where you want to mount /dev/sda5.

The location /mnt/shared_disk can be anything you want, really. Some people prefer /media/windows. The only thing is that the directory needs to exist before you run the mount command (nothing bad will happen, but the partition won't get mounted).

After you get this done, you should be able to browse in the file system to /mnt/shared_disk and see your files there. If that works, then we'll move on to the next step of editing /etc/fstab so that sda5 gets mounted automatically every time you boot up.

---

### Post by thelugnut on 2008-12-08
Thank you wylfing.

I am beginning to understand thanks to your clear explanation.

> After you get this done, you should be able to browse in the file system to /mnt/shared_disk and see your files there. If that works, then we'll move on to the next step of editing /etc/fstab so that sda5 gets mounted automatically every time you boot up.

I am ready to proceed here, whenever you can devote the time. I am so glad you included this last statement because that confused me also, as to why one would have to go through all that procedure every time one wanted to view some files. 

Can't thank you enough for helping me on this.):P

---

### Post by wylfing on 2008-12-08
Here's how you do it:
[LIST=1]
[*]If you already have sda5 mounted, unmount it now. You do this with the 'umount' command.
```
sudo umount /mnt/shared_disk
```
Where '/mnt/shared_disk' is wherever you decided to mount sda5.


[*]Make a backup of your /etc/fstab file in case anything goes wrong.
```
sudo cp /etc/fstab /etc/fstab_backup
```

[*]Open /etc/fstab for editing.
```
sudo gedit /etc/fstab
```

[*]Add a line that looks something like this to the end.
```
/dev/sda5 /mnt/shared_disk vfat iocharset=utf8,umask=000 0 0
```
Where '/mnt/shared_disk' is wherever you want sda5 to be mounted.


[*]Save and quit the editor.


[*]Run the "mount all" command.
```
sudo mount -a
```
[/LIST]

Your sda5 partition should be mounted, and it will always be mounted at boot-up time from now on.

Caveat: This is not *entirely* the right way to do this. The really right way is to set up group permissions and force the FAT32 partition to abide by those, so that only the users you specify have the power to read and write from your Windows disks. However, since you are booting into Windows part-time, and Windows doesn't enforce such measures, it's a moot point!

HTH, HAND

---

### Post by thelugnut on 2008-12-09
wylfing
That's pretty darn clear, my friend. I really appreciate your time and effort.

If there are any more "stone heads" out there that need help on this subject, I sure hope they find this thread.
:guitar:

Many thanks.

---

### Post by midijery on 2009-02-04
Thanks Your description of what to do was very helpful, but what about the UUID= numbers for the disk partitions are they needed ?
Jerry

---

