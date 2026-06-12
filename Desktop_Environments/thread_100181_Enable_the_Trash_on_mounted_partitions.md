---
title: "Enable the Trash on mounted partitions"
date: 2005-12-07
forum: Desktop Environments
---

### Post by lanjelot on 2005-12-07
Hi folks, 

When i delete a file from my ext3 mounted partition, it says it cannot move it to trash so it will delete it forever!

Is there a way to activate a Trash for mounted partitions? I am using nautilus btw.

Thx for your help...

---

### Post by lanjelot on 2005-12-07
Oh, and i forget to mention that i have the ownerships on the files of the mounted partition.

Here is how it looks:

$ ls -ld /home/seb/downloads
lrwxrwxrwx  1 seb seb   18 2005-12-02 19:39 downloads -> /mnt/hda6/seb-dls/

$ ls -ld /mnt/hda6/seb-dls
drwxr-xr-x  5 seb seb 4096 2005-12-06 10:48 /mnt/hda6/seb-dls/

Cheers

---

### Post by aysiu on 2005-12-07
I think this is fairly typical behavior, even on Windows.

For example, at work, we have a shared file server and our local hard drives. If I delete a file on my local hard drive, it goes into my Recycle Bin. If I delete it off the shared file server, it's gone forever.

You could always try "moving" it from the mounted partition to your trash.

---

### Post by lanjelot on 2005-12-07
ok thanks aysiu, but how do i do that ?

---

### Post by aysiu on 2005-12-07
[QUOTE=lanjelot]ok thanks aysiu, but how do i do that ?[/QUOTE] Do you have a middle-click button on your mouse? If so, find the file you want to trash (but not delete) and middle-click-drag it to the trash can. Once there, select "move here."

---

### Post by lanjelot on 2005-12-08
Ok thanks.

But i am actually looking for a way to make nautilus understand that when i delete a file (delete key, or the delete entry in context menu), it must move it to my .Trash folder.

Do you see a way to do that ?

thx again & bye

---

### Post by aysiu on 2005-12-08
My Nautilus has kind of a funky behavior. If I delete something from my MP3 player, it creates a hidden trash folder on the player itself for that file (when really I wanted it deleted completely).

I'm not sure how to enable that behavior you want.

---

### Post by doclivingston on 2005-12-08
What should happen is that a file will get moved to ~/.Trash if it's on the same partition as your home directory, and the ".Trash" folder in the top level of the partition is it's not. In the Nautilus options there is a preference which adds a "Delete" action that bypasses the trash.

There was recently some discussion on the Ubuntu-Devel mailing list about what should happen for removeable media, and the three options are basically:
1) move items to the ".Trash" folder on the removable media (what currently happens)
2) move it to ~/.Trash
3) delete it immediately

The problem with (1) is that some people (particularly those coming from Windows) assume that it will free the space immediately, and it doesn't.
The problems with (2) is that it means transferring all the data to the user home, which may be a) slow and expensive (large files, over a network), b) there may not be enough space on the partition or in their quota.
The problem with (3) is that things don't get moved to the trash, which is **Bad** if you expect to be able to remove things from the trash.

This issue never really got resolved, because each of the options has situation/users for which it isn't great,

---

### Post by lanjelot on 2005-12-09
Ok, thank you for your answers.

Now, I think you will understand what my problem is and maybe you can help me.

I actually want nautilus to go with the "a file will get moved to the ".Trash" folder in the top level of the partition" solution.

But there is no ".Trash" folder in the top level of the partition.

seb@lanjelot:/mnt/hda6$ ls -lA
total 24
drwxr-xr-x  2 root root  4096 2005-11-11 10:29 fedora-iso
drwx------  2 root root 16384 2005-11-11 10:26 lost+found
drwxr-xr-x  5 seb  seb   4096 2005-12-09 18:18 seb-dls

So i created a ".Trash" folder in /mnt/hda6 as follows:

seb@lanjelot:/mnt/hda6$ ls -ld .Trash
drwx------  2 seb  seb   4096 2005-12-09 18:18 .Trash

But nautilus still doesn't see it.
So, then i tried to change the ownerships to root:root

seb@lanjelot:/mnt/hda6$ ls -ld .Trash
drwx------  2 root root  4096 2005-12-09 18:27 .Trash

which doesn't work either.

So the question simply is how do i do to make the "deleted files will get moved to the ".Trash" folder in the top level of the partition" behavior doclivingston just described work ?

---

### Post by lanjelot on 2005-12-18
anyone ?

---

### Post by kanem on 2005-12-18
It may be the way your partitions are mounted. I have several mounted partitions and when I delete something from them it never gives me the 'must delete immediately' stuff. It just puts the file in the .Trash folder of that partition and also shows the trash icon on my desktop as being full. If I double click my trash icon I see the file. Here's part of my fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda8       /mnt/hda8       ext3    defaults,noatime        0       0
/dev/hda1       /mnt/windows    vfat    uid=k                 0       0

```
"k" is my username. I never had to make a .Trash folder for any partition. It did it automatically when I deleted something. I've deleted the .Trash folder before and another one gets made as soon as I delete something else.

---

### Post by jan-banan on 2005-12-18
[QUOTE=aysiu]My Nautilus has kind of a funky behavior. If I delete something from my MP3 player, it creates a hidden trash folder on the player itself for that file (when really I wanted it deleted completely).

I'm not sure how to enable that behavior you want.[/QUOTE]
this might be off topic but i found out that if i cut the file out of my ipod, it gets totally removed, but if i delete it it will get moved to a hidden folder. 

so just cut i out instead.

ps, i have no idea how to make the trashcan system work for you, ds

---

### Post by lanjelot on 2006-01-06
i've found out a way to make it work.

chown seb:seb /mnt/hda6

then since i own /mnt/hda6, /mnt/hda6/seb-dl and /home/seb and /home/seb/downloads -> /mnt/hda6/seb-dl

everystuff i delete from nautilus will go in /mnt/hda6/.Trash-seb

---

