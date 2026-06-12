---
title: "Network drives not appearing on Desktop"
date: 2008-04-25
forum: Desktop Environments
---

### Post by pholden on 2008-04-25
Since upgrading to Hardy Heron (8.04) this morning, my network drives (mounted via ncp) are not appearing on the desktop.

They are still mounting fine, but I'd like the icons back on my desktop 8-)

Another issue since upgrading is that when I visit various SFTP bookmarks through nautilus, they DO appear as icons on my desktop, which I really don't want.

In the screenshot, *M-Drive* and *R-Drive* previously had icons on the desktop, and the *sftp on x* didn't used to get one.

How can I revert to Gutsy Gibbon behaviour?

Paul

---

### Post by LavosPhoenix on 2008-04-25
I'm having the same problem, except I'm using xubuntu. I really need a solution to this problem.

---

### Post by WakkiTabakki on 2008-04-28
+1 with regular Ubuntu...

/N

---

### Post by pholden on 2008-04-28
I found the answer to the first question in [this thread]("http://ubuntuforums.org/showthread.php?t=771057") - mount them outside of /mnt to get the Desktop icons.

Would still like to know how to prevent getting Desktop icons everytime I connect to an SFTP server though.

---

### Post by WakkiTabakki on 2008-05-04
Yup, that did it. Thanks!

---

### Post by LavosPhoenix on 2008-05-11
No, that did not work for me. My drives are ALREADY mounted in /media, and always have been. Which is why I brought up this issue, as the icons NO LONGER APPEAR on my desktop as they did in 7.10 and previous versions. This is what I want fixed, as now my drives no longer show up on the side panel of Thunar as they did previously. No, I don't want a shortcut hack, that doesn't show the drive icons.

---

### Post by siddharth_moghe on 2008-05-21
Lavos - both of us are facing the same problem. Even my disks dont mount at all . Although the external sata drive i use always shows up on the desktop unlike the other internal existing windows partition and the most annoying part is that even in fstab if included they dont show up in media at all - let alone the desktop icons !

when i use ntfs-3g to install them - then give an errors ( unmount them from media before i use ntfs )

Nor do they mount in media nor in mnt

Now guys we have specific questions here. I would req the users to please be specific with their answers !:confused::frown:

---

