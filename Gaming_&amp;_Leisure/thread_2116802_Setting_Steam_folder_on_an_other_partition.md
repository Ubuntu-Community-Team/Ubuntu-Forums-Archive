---
title: "Setting Steam folder on an other partition"
date: 2013-02-16
forum: Gaming &amp; Leisure
---

### Post by Matt92HUN on 2013-02-16
Hi, I'm trying to set up a folder for my steam games on a partition, where I have more space, but it says "New Steam library must be on a filesystem mounted with execute permissions". When I try to change the permissions from properties, it doesn't let me and doesn't even give a message, why. I'm not really familiar with linux, so I guess I'm missing something obvious. Could somebody help?

---

### Post by Perfect Storm on 2013-02-16
I have Steam (and all other games) on another partition. The /games partition :P

There's different ways to give you access to that partition. The click'n'point way:

1. <alt>+<F2>
2. write: gksu nautilus
3. Find the partition in your system /
4. right click on that folder ---> properties ---> permissions
5. Set owner to user - you
6. Set access to 'Create and Delete files
7. You may click 'Apply Permission to Enclosed Files'.
8. exit/close the file browser

**[COLOR="Red"]NB:[/COLOR]** Just be careful. Never use gksu nautilus for normal stuff, you can easily bork your system or compromise the security if you don't know what you're doing.

---

### Post by Matt92HUN on 2013-02-17
> **Artificial Intelligence said:**
> I have Steam (and all other games) on another partition. The /games partition :P

There's different ways to give you access to that partition. The click'n'point way:

1. <alt>+<F2>
2. write: gksu nautilus
3. Find the partition in your system /
4. right click on that folder ---> properties ---> permissions
5. Set owner to user - you
6. Set access to 'Create and Delete files
7. You may click 'Apply Permission to Enclosed Files'.
8. exit/close the file browser

**[COLOR="Red"]NB:[/COLOR]** Just be careful. Never use gksu nautilus for normal stuff, you can easily bork your system or compromise the security if you don't know what you're doing.

Whatever I try to change there it just reverts to the original setting. It's formatted in NTFS and has been previously used by Windows, could that be a problem?

---

### Post by Perfect Storm on 2013-02-17
> **Matt92HUN said:**
> Whatever I try to change there it just reverts to the original setting. It's formatted in NTFS and has been previously used by Windows, could that be a problem?

Aye, You need to use a linux partition (like ext4). You can use an application like gparted to change that partition.

---

### Post by Matt92HUN on 2013-02-17
> **Artificial Intelligence said:**
> Aye, You need to use a linux partition (like ext4). You can use an application like gparted to change that partition.

I see. Can I just take some of it and format it in ext4, while keeping the files I have there?

---

### Post by Perfect Storm on 2013-02-17
> **Matt92HUN said:**
> I see. Can I just take some of it and format it in ext4, while keeping the files I have there?

I'm not sure if you have to defrag it first under Windows first, and also depending how much Windows use compared to what you take. Perhaps ask someone else, Windows is not my strong side :p

---

### Post by efflandt on 2013-02-17
As long as it is a conventional msdos partition, you could defrag the ntfs partition in Windows first.  Then use **gparted** to shrink it and make a Linux partition (like ext4) in the unallocated space. I cannot tell you how to do it if the partition is a Windows volume or gpt partition.

Then once you configure /etc/fstab to properly mount the new Linux partition automatically on /media you could
```
cp -r ~/.local/share/Steam /media/otherpartition/Steam
sync
rm -r ~/.local/share/Steam
ln -s /media/otherpartition/Steam ~/.local/share/Steam
```But check that data was successfully copied and is owned by you before the **rm**, and don't forget the dot in "**.local**". That makes a symbolic link to where you put the data on the other partition.

---

### Post by Matt92HUN on 2013-02-19
> **efflandt said:**
> As long as it is a conventional msdos partition, you could defrag the ntfs partition in Windows first.  Then use **gparted** to shrink it and make a Linux partition (like ext4) in the unallocated space. I cannot tell you how to do it if the partition is a Windows volume or gpt partition.

Then once you configure /etc/fstab to properly mount the new Linux partition automatically on /media you could
```
cp -r ~/.local/share/Steam /media/otherpartition/Steam
sync
rm -r ~/.local/share/Steam
ln -s /media/otherpartition/Steam ~/.local/share/Steam
```But check that data was successfully copied and is owned by you before the **rm**, and don't forget the dot in "**.local**". That makes a symbolic link to where you put the data on the other partition.

I can only increase the size from Gparted, am I missing something?

---

### Post by dannyboy79 on 2013-02-19
> **Matt92HUN said:**
> I can only increase the size from Gparted, am I missing something?the partition has to be unmounted in order to change it. when in gparted, you click on the partition and right click should show "resize"

i would make sure you back up any critical files first before using gparted to shrink a NTFS partition. GOod luck

---

### Post by efflandt on 2013-02-19
If you have Windows Vista or 7 you could also use administrative tools in that to shrink the ntfs partition.  But as mentioned, if using gparted the partition has to NOT be mounted in order to shrink it.

---

### Post by Matt92HUN on 2013-02-22
> **efflandt said:**
> If you have Windows Vista or 7 you could also use administrative tools in that to shrink the ntfs partition.  But as mentioned, if using gparted the partition has to NOT be mounted in order to shrink it.

I could shrink it from Windows, thanks.

---

### Post by Horbo on 2013-06-19
Frustrating....!

I have a folder(mount point) called  /storage that I mount an ext3 partition on.  The partition has on it a folder called SteamLibrary that I want to install steam games in, because I've run out of space on my old partition, and don't want to resize it.

But when I go into steam's settings and tell it to add this location as a library folder, I get the 
"[COLOR=#000000]*New Steam library must be on a filesystem mounted with execute permissions*" 
error and it fails.

Here are the permissions of the mount point before mounting:
[/COLOR]```
drwxrwxrwx   2 infin root     4096 Dec 20 19:39 storage/
infin@infin-MCP61M-M3:/$
```
[COLOR=#000000]No permission restrictions there.


And after mounting:
[/COLOR]```
drwxrwxrwx   4 infin root     4096 Jun 19 15:45 storage/
infin@infin-MCP61M-M3:/$
```
Full permissions given.


And of the actual target folder: 
```
drwxrwxrwx  3 infin infin  4096 Jun 19 21:26 SteamLibrary/
infin@infin-MCP61M-M3:/storage$ 
```
Full permissions given.



And here is the fstab line that mounts it: 
```
UUID=ae38e823-a0b0-4b18-bc44-ef9411500e6f /storage        ext3    rw,suid,dev,exec,auto,user,async,noatime        0       2
```

Steam's cause for complaint is a complete mystery to me!  As far as I can tell I'm giving full permissions everywhere possible, what on earth is wrong??
[COLOR=#000000]

[/COLOR]

---

### Post by Horbo on 2013-06-20
No ideas?

---

### Post by cody1233 on 2013-06-21
If you keep having problems, I would recommend downloading a disk image of the GParted live CD and running that...

---

### Post by Horbo on 2013-06-21
> **cody1233 said:**
> If you keep having problems, I would recommend downloading a disk image of the GParted live CD and running that...

I have one that I keep handy, but I don't see how that'll help with Steam related permissions?

---

### Post by Redsandro on 2013-11-18
This is annoying, I have exactly the same problem.

I was running **Ubuntu 12.10** on SSD with a Steam library on a NTFS HDD. It contains a LOT of games. No problems.

Now I installed **Ubuntu 13.10**, installed Steam, nothing physically changed and suddenly I cannot add this library because of blah blah.

Isn't there some file I can edit to forcefully add this NTFS filesystem library folder to Steam? Because I think the complaining is just BS - it worked before.

---

### Post by oldfred on 2013-11-18
Are you permanently mounting with fstab? If not defaults probably do not include execute permissions. And normally we do not want excute permissions floating around as then you may compromise secuity. One of the main advantages of Linux over Windows is the logic behind ownership and permissions.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by Redsandro on 2013-11-18
Everything is automatically mounted under my username and group in Ubuntu 13.10. (In 12.10 you had to do that manually.)

But you are right! I think*.
I just recreated the exact same mount in **fstab** as I had before the upgrade and all my games are back in Steam.

*) So the library was already set in preferences, I haven't tested actually *adding* it because I don't want to risk not being able to add it after I remove it just for testing.

Anyway thanks for suggesting fstab. :)

---

