---
title: "USB Drive Permissions"
date: 2006-07-27
forum: Desktop Environments
---

### Post by DoodlesQ on 2006-07-27
I've seen a lot of variations on this question asked, but nothing that quite fits my specific details. 

I have a USB drive external drive that's working fine from the laptop itself. Great.

I'm running XBox Media Center (XBMC) downstairs. XBMC has no problem playing my Samba shares from the laptop drive, but can't acccess the external drive. 

I'm certain that this is related to the drive not having read permissions for 'others' and 'group.' I know because when I copied a file from the external drive to the laptop drive, it carried withit the laptop permission set (where  I, the user, have read/write but nobody else does). XBMC refused to play those files. When I added read permissions for others and group, they worked again.

So what I need to do is give the group/other access to the laptop drive. However, when I try to change the permissions through naitlus, the boxes simply uncheck themselves. I tried it through the command line, and still got errors.

I added umount=0000 to the line that mounts the drive in Fstab (on the advice of a friend). That still isn't working. So the drive's line in fstab looks like this:
```
/dev/hda3	/home/jeff/media	ext3	defaults,umask=0000	0	0
```

Still can't change the permissions though. I'm sure there's something simple, can anyone help?

---

### Post by DoodlesQ on 2006-07-27
Wait, I figured it out. That last line wasn't my external hard drive. And I thought I was so smart.

I've come a long way to understanding this stuff, but still not there. Thanks again everybody!

---

