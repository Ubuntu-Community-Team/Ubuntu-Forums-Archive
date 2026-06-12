---
title: "How to remove mount symbol from desktop?"
date: 2008-05-04
forum: Desktop Environments
---

### Post by nivosh on 2008-05-04
hello.

can i remove the mount symbol of the internal drives from the desktop but still keep them mounted?

---

### Post by ad_267 on 2008-05-04
Run gconf-editor and then go to apps - nautilus - desktop and uncheck volumes visible

---

### Post by nivosh on 2008-05-04
thanks man!

it worked...

---

### Post by ad_267 on 2008-05-04
Cheers. I should point out that if you put in a CD or flash drive this will not show up either now. I think the only way to get them to show up and not your internal drives is to mount the drives somewhere other than /media.

---

### Post by Vivaldi Gloria on 2008-05-04
If you don't want to get a drive icon on the desktop then the best thing to do is edit your /etc/fstab to mount the drive to /mnt/mountpoint and then put a link to where ever you want.

---

### Post by ShanaVar on 2008-05-06
I posted a question like this before but noone could help me. I mounted the partition into my home directory but still get the icon on the desktop. Is there any workaround?

Greets

---

### Post by ad_267 on 2008-05-07
It's probably still being mounted in /media. You will need to edit the file /etc/fstab and change the mount point there.

---

### Post by ShanaVar on 2008-05-11
done that. mount command gives the following:

/dev/sdb1 on /home/shanavar/Video1 type ext3 (rw)

still, i got the icon on the desktop

---

