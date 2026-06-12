---
title: "ext4 backup, and disk space used"
date: 2009-05-22
forum: General Help
---

### Post by dave31175 on 2009-05-22
Gparted reports 3.64GB used on sda1 (ext4 formatted). I'm wanting to back up that partition. Attempts to use Clonezilla have resulted in an extremely unhelpful "Something went wrong" error. I found this command on another post and have tried it:

```
sudo dd if=/dev/sda1 | gzip > /home/d/backup/system_drive_backup.img.gz
```

The result of the command (after several hours) was this:

```
^C38775873+0 records in
38775872+0 records out
19853246464 bytes (20 GB) copied, 17031.7 s, 1.2 MB/s

```

The filesize of the file system_drive_backup.img.gz is 15GB. How can this be if only 3.64GB is used on sda1?

---

### Post by kpkeerthi on 2009-05-22
The image, when not compressed, created by dd is as big as the size of the partition.

---

### Post by colau on 2009-05-22
> **dave31175 said:**
> Gparted reports 3.64GB used on sda1 (ext4 formatted). I'm wanting to back up that partition. Attempts to use Clonezilla have resulted in an extremely unhelpful "Something went wrong" error. I found this command on another post and have tried it:

```
sudo dd if=/dev/sda1 | gzip > /home/d/backup/system_drive_backup.img.gz
```

The result of the command (after several hours) was this:

```
^C38775873+0 records in
38775872+0 records out
19853246464 bytes (20 GB) copied, 17031.7 s, 1.2 MB/s

```

The filesize of the file system_drive_backup.img.gz is 15GB. How can this be if only 3.64GB is used on sda1?

What was the problem with Clonezilla?

---

### Post by dave31175 on 2009-05-22
> **kpkeerthi said:**
> The image, when not compressed, created by dd is as big as the size of the partition.

Thanks, but now I'm more confused.

The partition is approx 74GB total. 
dd said 20GB was copied (assuming pre-compression 20GB)
gparted reports only 3.64GB of the partitions is "used"

I would have expected the pre-compressed backup to be equal to the "Used" portion, OR based on your statement, the pre-compressed backup should be 74GB equal to the entire partition. Both are a long way from the 20GB pre-compressed amount of data reported as copied.

---

### Post by Cracauer on 2009-05-22
You cannot safely backup a read-write mounted filesystem by copying the raw device underneath. In your case it's even worse since you don't even have a snapshot in time.

---

### Post by mellowd on 2009-05-22
But you compress it, therefore 74GB compressed is 20GB

---

### Post by dave31175 on 2009-05-22
> **colau said:**
> What was the problem with Clonezilla?
I don't know -- the only error message was "Something went wrong". It said more information could be found in a log file that didn't exist. I could see that it started to write data to the destination specified, but after only a few seconds it aborted with the "Something went wrong" message. 

The only thing I could come up with was that it required the destination to have as much free space as the entire partition it was backing up and aborted when it found that wasn't the case. If that really is the reason, it seems silly that it would require 74GB to make a compressed image of 3.64GB of data, so I'm hoping my hypothesis is wrong.

---

### Post by dave31175 on 2009-05-22
> **Cracauer said:**
> You cannot safely backup a read-write mounted filesystem by copying the raw device underneath. In your case it's even worse since you don't even have a snapshot in time.

Makes sense. Any suggestions? Clonezilla's "Something went wrong" error message doesn't give me much to go on for troubleshooting. Partimage seems highly recommended but doesn't work with ext4. fsarchiver has been mentioned, but I could only find where that needs to be compiled from source, and I was hoping to avoid that, noob that I am...

---

### Post by dave31175 on 2009-05-22
> **mellowd said:**
> But you compress it, therefore 74GB compressed is 20GB

The final file-size was 15GB. dd reported copying 20GB data?

---

### Post by logos34 on 2009-05-22
since you have so much free space, try clonezilla again, it only copies the USED sectors, which should result in a very small .gz image...dd copies even the unused parts (which is fine for nearly full partitions, where you're going to want to copy everything anyway)...+1 for what mellowd said...

maybe do a fsck beforehand or enable check option in clonezilla (or does it do it by default?)...not sure what's causing the error

---

### Post by logos34 on 2009-05-22
only the Clonezilla ['Testing (beta)' version ]("http://www.clonezilla.org/") (and Ubuntu experimental vers.) supports ext4--is that the version you're using?

> 
Clonezilla (Ubuntu experimental)
* Ext4 is supported by partclone now. Therefore if you want to save ext4 system, remember to enter expert mode and use option -q2 so that partclone will save your ext4 partition.
[http://ubuntuforums.org/archive/index.php/t-1122892.html](http://ubuntuforums.org/archive/index.php/t-1122892.html)


---

### Post by dave31175 on 2009-05-22
> **logos34 said:**
> since you have so much free space, try clonezilla again

I'll do that. I think I just found the problem:

[http://sourceforge.net/forum/forum.php?forum_id=957311](http://sourceforge.net/forum/forum.php?forum_id=957311)
> Ext4 is supported by partclone now. Therefore if you want to save ext4 system, remember to enter expert mode and use option -q2 so that partclone will save your ext4 partition.

I was using beginner mode. I'll try Clonezilla again using these instructions.

---

### Post by dave31175 on 2009-05-22
> **logos34 said:**
> only the Clonezilla ['Testing (beta)' version ]("http://www.clonezilla.org/") (and Ubuntu experimental vers.) supports ext4--is that the version you're using?

That was the version I used, however it apparently couldn't do ext4 from "beginner" mode. According to the sourceforge link I posted in my previous post, today's stable release has ext4 support, but still requires "advanced" mode. With this in mind I'll give it another try.

Thanks all for your help and suggestions. This forum is an incredible resource!

---

### Post by logos34 on 2009-05-22
> **dave31175 said:**
> According to the sourceforge link I posted in my previous post, today's stable release has ext4 support, but still requires "advanced" mode.

hmm, ok..I just wish they'd update the Clonezilla homepage:

> Filesystem supported: ext2, ext3 (ext4 is supported now in testing branch)...

---

### Post by dave31175 on 2009-05-22
> **logos34 said:**
> hmm, ok..I just wish they'd update the Clonezilla homepage:
Their homepage seems to leave a bit to be desired all around...

---

### Post by Cracauer on 2009-05-22
Why would you use a beta version some *zilla or another (for backups of all things), when tar or dump pretty much does what you want?

---

### Post by VMC on 2009-05-22
Dave,
I use the "20090517-jaunty" Clonezilla and just the beginner mode. "q2" is automatically selected now.

There's one note to make using Clonzilla. You can restore to different drives but not to different partitions. That's easily resolved using Partclone program itself though.

Also, are you sure you selected saveparts and not savedisk?

Please do the following so we can following along. After you have selected all your info, you will be brought to "yellow" text, just before it starts imaging, that states in the future you can use this message directly. At that point either write down the ocs message exactly or open another console using Alt+F2. to to "/tmp" dir and cat out the osc* message. You can even cp it to the local-dev for save keeping.

Bring that ocs message back here so we can examine it.

---

### Post by mellowd on 2009-05-23
> **Cracauer said:**
> Why would you use a beta version some *zilla or another (for backups of all things), when tar or dump dpes pretty much does what you want?


+1

tar+gz is the winner

---

