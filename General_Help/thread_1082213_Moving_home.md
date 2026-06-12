---
title: "Moving home"
date: 2009-02-27
forum: General Help
---

### Post by FraggedLocust on 2009-02-27
I want to move my home directories over to a separate partition. I didn't get an option in Guided like Debian or Fedora. Would it work if I just resize and make a partition (ext3?) last time i did something to my home i locked my configurations and admin account. Mind, i did make it a hidden folder.

---

### Post by smani on 2009-02-27
First, create the partition you want to move your home directory to. Then, copy over your home directory, and then add an entry to /etc/fstab to mount the partition to /home, such as

UUID=partition_uuid /home ext3 relatime 0 2

where you can find out the partition_uuid by running
```
sudo blkid
```

Reame the original /home directory to /home_bak so that you won't get any errors concerning non-empty mount-points, then create a new empty directory home
```

sudo mkdir /home
```
and finally reboot the system. If everything worked out fine, your new partition containing your home directory should be mounted into /home. If that is the case, you can delete the /home_bak folder.

---

### Post by FuturePilot on 2009-02-27
I used [this guide]("http://www.psychocats.net/ubuntu/separatehome") when I moved my /home to a separate partition. It worked very well.

---

### Post by FraggedLocust on 2009-02-27
I would like to merge some unallocated space on the disk that is outside the ntfs partition for windows with my linux partition's unallocated space inside the logical partition. Is this possible?

---

### Post by FraggedLocust on 2009-03-03
> **FuturePilot said:**
> I used [this guide]("http://www.psychocats.net/ubuntu/separatehome") when I moved my /home to a separate partition. It worked very well.

when I run this line:

find . -depth -print0 | cpio --null --sparse -pvd /mnt/new/

I get lots of:
 Cannot stat: No such file or directory

and
 Cannot make directory `X': permission denied

The weird thing I noticed was the output was using the character on the tilde key (`) as one of the single quotes ('). Is this normal?

---

### Post by FraggedLocust on 2009-03-04
> **smani said:**
> If everything worked out fine, your new partition containing your home directory should be mounted into /home. If that is the case, you can delete the /home_bak folder.

So now any users I create will go to the new partition because it's automounted on startup?

---

