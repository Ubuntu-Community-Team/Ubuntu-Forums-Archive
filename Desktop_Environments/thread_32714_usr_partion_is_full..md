---
title: "/usr partion is full."
date: 2005-05-09
forum: Desktop Environments
---

### Post by norwyn on 2005-05-09
My /usr partion is full. How do I direct synaptic to install in various partions? How can I make the /usr partion bigger? Thanks in advance.  ](*,)

---

### Post by tread on 2005-05-09
I don't know how to do this .. but I can suggest a direction to explore.

Linux Volume Manager: I guess you will need to create a group for /usr, and then add partitions to it. Since /usr is then "virtual", it can contain different partitions/hard disks/maybe even different directories.

And if you do get everything setup nicely, please do write a small HOWTO :)

---

### Post by tonym on 2005-05-09
The answer to this will depend on your existing layout.  What partitions have you got?  What is their size?  Have you any empty space,  if so where? There are a number of options:

Resize the existing partition.  This may require you to move other adjacent partitions.  There is a tool "parted"  which can do this.  This can take some time and can be risky.

If you have space,  create a new larger partition, copy the contents of your existing /usr to it then edit /etc/fstab to point to the new partition.

Create a new partition and copy part of /usr to it  -  /usr/local say if it is significant.  Delete that part from your existing partition then mount your new partition at that point.

LVM is a good tool and would make this easier to solve.  Unfortunately you need to start off with LVM before you have the problem.  You could only use it now if you have spare space large enough to take the existing /usr.  This doesn't need to be contigous or even on the same disc.  LVM would be a good idea if you were thinking of getting a new disk.

Hope this is of some help.

Regards

Tony.

---

