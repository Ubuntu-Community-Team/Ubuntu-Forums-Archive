---
title: "Permission"
date: 2009-05-28
forum: General Help
---

### Post by texas.chef94 on 2009-05-28
Jaunty is installed on HD. I have an external USB as well with 2 media partitions that were functioning great. They were ext4 (do not as why I just did it) Anyway I installed Lenny to this same external, but debian would not recognize these storage partitions in ext4 so I changed them to ext3 not realizing that entailed format as well, I do have that lost info backed up to CD, but someone tell me how to regain ownership which I lost in the transition.

Thanks

Allen

---

### Post by khelben1979 on 2009-05-28
Are you saying that you can't access the files on the external usb disc because of the transition from EXT4 to EXT3? If all the files are backed up to another disc you should just reformat the drive using EXT3, I think, and then just copy them over.

With the sudo command you should be able to access all the files and change permissions on them as you will. 

I'm not sure if this was helpful, but I tried. :-|

---

### Post by mikewhatever on 2009-05-28
Here is a thread that deals with the same problem.
[http://ubuntuforums.org/showthread.php?t=1172365](http://ubuntuforums.org/showthread.php?t=1172365)

---

### Post by texas.chef94 on 2009-05-28
> **khelben1979 said:**
> Are you saying that you can't access the files on the external usb disc because of the transition from EXT4 to EXT3? If all the files are backed up to another disc you should just reformat the drive using EXT3, I think, and then just copy them over.

With the sudo command you should be able to access all the files and change permissions on them as you will. 

I'm not sure if this was helpful, but I tried. :-|

It would be I guess had I not given you impression I know more then I do.
So sdb1 ext3 /media/disk-1 and sdb2 ext3 /media/disk both need to be owned by me allen read/write whole works.
If you will give me the terminal commands based on above.

please advise

---

### Post by texas.chef94 on 2009-05-28
Sorry to have not figured it out myself. Solved
sudo chmod 777 /media/disk-1 then same thing with /media/disk

Allen

---

