---
title: "Can't get Extended Attributes to work"
date: 2009-05-05
forum: General Help
---

### Post by nordlöw on 2009-05-05
Hey there, Ubuntu Lovers!

I can't get extended attributes (xattr) to work on my ext4 root partition having Jaunty 32-bit installed.

I have edited the root entry in my [FONT=Courier New]/etc/fstab[/FONT] as follows.

[FONT=Courier New]proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
**UUID=f016ca25-6ca9-4547-9318-c016178afbd5 /               ext4    relatime,errors=remount-ro[COLOR=DarkOrchid],user_xattr,extents,acl[/COLOR] 0       1**
# swap was on /dev/sda2 during installation
UUID=85b04026-3b39-4fd9-aeff-05a62077d8d2 none            swap    sw              0       /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
[/FONT]
But when I try to set an extended attribute using the example
[B][FONT=Courier New][COLOR=DarkGreen]setfattr -n name -v val ~/.bashrc[/COLOR][/FONT]
[/B]it fails with the error message
[FONT=Courier New][COLOR=Red]**setfattr: /home/per/.bashrc: Operation not supported**[/COLOR][/FONT]

I have verfied that my changes to fstab has been read by the system using:
[COLOR=Green]**[FONT=Courier New]mount|grep xattr[/FONT]**[/COLOR]
which gives the result
[COLOR=Green]**[FONT=Courier New]/dev/sdb1 on / type ext4 (rw,relatime,errors=remount-ro,user_xattr,extents,acl)[/FONT]**[/COLOR]

I believe this used to work on my previous Intrepid installation using ext3. Is ext4 the problem or  have I missed something else?

Thanks in advance,
Per Nordlöw

---

### Post by mal on 2009-12-24
Nordlöw,

I have been looking at extended attributes for storing metadata for photos and came across your post.  It seems strange to me that there is not more interest in extended attributes.  

For your information, I have successfully enabled extended partitions on my Karmic system.  I simply included "user_xattr" in the fstab options for an ext4 partition that I use for storing shared information and I was able to set and read extended attributes for an image file.

I would be interested to hear if you are still having problems.

Regards,

Mal

---

### Post by jonls on 2009-12-29
> **nordlöw said:**
> But when I try to set an extended attribute using the example
[B][FONT=Courier New][COLOR=DarkGreen]setfattr -n name -v val ~/.bashrc[/COLOR][/FONT]
[/B]it fails with the error message
[FONT=Courier New][COLOR=Red]**setfattr: /home/per/.bashrc: Operation not supported**[/COLOR][/FONT]
When using setfattr to set extended attributes one should prefix the attribute name with "user.".
```
setfattr -n user.name -v val file
```

---

### Post by sehe on 2010-06-30
splendid thanks, for that explanation, much needed!

Prefixing with user. was the solution indeed

---

