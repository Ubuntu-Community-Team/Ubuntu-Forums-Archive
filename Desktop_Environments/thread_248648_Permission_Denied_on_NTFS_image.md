---
title: "Permission Denied on NTFS image"
date: 2006-09-01
forum: Desktop Environments
---

### Post by ineluki12 on 2006-09-01
I'm attempting to access a bit-for-bit image of an NTFS partition. The mount appears to work, but it tells me 'Permission Denied' when I try to cd or ls. Has anyone else encountered something similar? Here's my fstab entry:

```
/mnt/maxtor300/sda1.img	/mnt/maxtor300/mnt/sda1	ntfs	loop,defaults,user,noauto,ro	0	0
```

Thanks!

---

### Post by Lunar_Lamp on 2006-09-01
Have you tried to "ls" with sudo? (sudo ls)

If that fixes it, you can make yourself the owner of the file with chown, or modify the file access attributes with 'chmod'.

---

### Post by galileon on 2006-09-01
hello, i just came across this yesterday

[http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697](http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697)

but unfortunately (or FORTUNATELY? :):) hehe) i dont have ntfs partitions and probably will never have them again (im sticking with linux now!) - so i cant try it out...

let us know if it works for you!
cheers

---

### Post by ineluki12 on 2006-09-01
I tried both sudo ls and sudo cd and got the 'can't find ls' and 'can't find cd' errors. Would this have to do with a config file for sudo?

Also, I really couldn't care much less about writing and editing an ntfs partition. I'm just wanting to analyse this image. Does the ubuntu Kernel normally have the read-only ntfs driver built into it?

---

### Post by galileon on 2006-09-01
ls and cd are a bit like cd and copy in DOS - they are commands that bash itself interpretes, while sudo gnome-thingy means ask for root passwd, then run gnome-thingy with root priviledge...in this case, gnome-thingy is an external program, whicl sudo will look for (probably in /bin, /usr/bin, /usr/local/bin, etc)


if you want to ls, or cd with root priviledge, do a sudo -s first, this will give you a root console - but remember - with great powers come great responsibilities...

---

### Post by ineluki12 on 2006-09-01
Ah, good call galileon. That works well. Does the system deny access to all users except root because it doesn't understand the ntfs permissions?

---

### Post by galileon on 2006-09-01
i suppose you could try a chown user_foo /mnt/bar, where /mnt/bar is the place you mounted it, to give ownership to user_foo...

or you could try

chmod o+rwx /mnt/bar

to give everyone on the system access to read/write/display whatever is in /mnt/bar

---

### Post by ineluki12 on 2006-09-01
I did chmod 777 the mount point. I suppose I could chown it, but I don't anticipate having any luck with that.

---

