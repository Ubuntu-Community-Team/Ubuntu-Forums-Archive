---
title: "(some of) my hard drive has gone missing!"
date: 2009-01-09
forum: General Help
---

### Post by Darth_tater on 2009-01-09
(some of) my hard drive has gone missing!

Help!  I recently added a 300 GB hard drive to my file server so I could do network based backups.  I added the hard drive, formatted it with G parted and then created a fstab entry and made a samba share.

So far so good, right?  Well, no.  see, it&#8217;s a 300 GB drive so about 270 gb should be free after formatting, but the folder that I mounted the drive as only has a capacity of 10 GB!!!!?!
What did I do wrong?  Why is it not working?  Where did ~ 260 GB of hard disk space go?!?!?

===========================
Here is my /etc/fstab file
===========================
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=92304a8c-b321-46d5-9d20-850abc1b1725 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=aa3ae510-517f-49ad-8e0a-9efb4d0850b4 /home           ext3    relatime        0       2
# /dev/sda3
UUID=f4bed53a-b764-4b1b-9267-9b9f757f94a0 none            swap    sw              0       0
# /dev/sdb5
UUID=22111344-81bb-45b5-960c-40f9226828d4 none            swap    sw              0       0
# /dev/sda1
/dev/sda1	/backup 	ext3	realtime


Thanks for any and all help!

---

### Post by taurus on 2009-01-09
Are we talking about the /dev/sda1?  Personally, I would replace the entry for it in /etc/fstab with this one.

```
/dev/sda1   /backup   ext3   defaults   0   2
```
Otherwise, post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by Darth_tater on 2009-01-09
yes, i am talking about sda1.

Riiight.  I should have been more specific.

The *last* entry in the fstab file is what I just added to get my new hard drive working.

Ill post back with the results. Could you explain the changes you made, though?

---

### Post by Darth_tater on 2009-01-09
cool!  I had to redo some things to fix some errors, but I got it working.  Now I see a full 260.9 GB free in my  /backup folder.

Thanks!  Can you just explain what the changes did?

---

