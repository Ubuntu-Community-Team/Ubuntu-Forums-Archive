---
title: "Free space...? No Free space??"
date: 2009-05-20
forum: General Help
---

### Post by jorwex on 2009-05-20
I haven't posted here in a while with a problem, but I'm a bit out of touch. I updated to Jaunty. I had a number of ext3 partitions and decided to move some music to a fat32 partition so it'd be more cross-OS happy. So I created the fat32 partition (Music, below) and moved stuff over from the ext3 partition it was on, and then deleted the data from teh ext3 partition when it was done. I emptied the trash and for kicks I even checked the ./Trash-xxxx folder and deleted the files from there. 

Now the fat32 partition is happy, but the old ext3 one it was on before says there's no free space...except gparted says it does...see the pic below:

[IMG]http://dc139.2shared.com/download/5879237/ec661379/Screenshot2.png?tsid=20090520-230924-1087f538[/IMG]

What's wrong?

---

### Post by damis648 on 2009-05-20
Please, do not embed such large images in posts. It is relatively annoying. Try the following, there may be a filesystem problem:
Open a terminal and:
```
sudo umount /dev/sda6
sudo fsck /dev/sda6
```
and have it check for errors on the partition's filesystem. If it turns up anything, tell it to fix it, and if not, then post back.

---

### Post by cholericfun on 2009-05-20
that is odd,
especially since you only needed a very small amount of disk space there..
doesnt make much sense but did you try a reboot?

---

### Post by jorwex on 2009-05-22
sorry about the pic. it was easier at the time to just put it there instead of describe it in detail.

anyway, it's clean:

```
~$ sudo umount /dev/sda6
~$ sudo fsck /dev/sda6
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Data: clean, 42357/32661504 files, 126138740/130616474 blocks

```

---

### Post by jorwex on 2009-05-23
What else can I check?

I do remember when i was in the .Trashes-1000 folder, it kept making the Music folder that I was attempting to delete reappear when I highlighted it and pressed the delete button. I had to shift-delete to get rid of it. 

However, there's no .local folder in Root's directory (which if you go deeper is supposed to be where root's trash dir. is). 

**Still tho, why would gparted show the free space when nothing else will? **

---

### Post by KhurramM on 2009-05-23
Can u reformat this partition, better use gparted.

See if this solves your issue. :)

---

### Post by kimda on 2009-05-23
If this directory is personal files and not system files you can install fslint and let it search for duplicate files. When its finished select the duplicate you want to delete and press delete.

---

### Post by jorwex on 2009-05-27
No dupes for the music :(

I did find about 2 gigs of unrelated duplicates tho! Neat tool.

Is there anything anyone can think of that will let me avoid backing up and reformatting this GIGANTIC partition? I don't have another drive to back up 498 GB.

THanks for the continued help

---

### Post by PGScooter on 2009-05-29
check out the tool filelight

It is great at showing you where your space is going.

---

### Post by jorwex on 2009-06-19
I've tried a couple of those pie charting space showing programs.

The problem is, they don't show the space being used because it *isn't* being used (I think).

There's a deeper problem here. Can anyone think of any other causes? 

Something to remember that may provide a hint: gParted remains the only program that shows that the free space is present.

See:
[http://dc139.2shared.com/download/5879237/ec661379/Screenshot2.png?tsid=20090520-230924-1087f538]("http://dc139.2shared.com/download/5879237/ec661379/Screenshot2.png?tsid=20090520-230924-1087f538")

---

### Post by jerome1232 on 2009-06-19
ext3 does reserve 5% of the space for root user by default. Maybe that's what your running into. I'm pretty sure Gparted is showing partition size/free space not file system size/free space.

So really the ext3 file system will be about 5% smaller than the partition, this isn't counting the small amount of space needed for inodes and the journal and etc...

---

### Post by ugm6hr on 2009-06-19
Check with df.  Mount the drive, then:

```
df -h
```

I have seen this once before (pre-Hardy), and found the easiest solution was to reformat the partition.

I thought that modern Ubuntu's prevented you from completely filling a partition to 0 bytes free, since once you get to that stage, it is a real problem to recover from.

Presumably you had 0 bytes free before you moved the media to the FAT partition?

---

### Post by hibliss on 2009-06-19
If the folder you deleted them from was owned by root, they could have ended up in the root trash. That happened to me before.

```
gksudo nautilus /root/.local/share/Trash/files
```

And see if there is anything in that folder.

---

### Post by jorwex on 2009-06-19
@ugm6hr
I thought I left a little bit of space in there before. I could be wrong though. Why is that a problem? Do you have any more info on that? It's my biggest partition, with all my media...I don't have anywhere else to put it :(

@hibliss
checked there first :)

keep em coming!

---

