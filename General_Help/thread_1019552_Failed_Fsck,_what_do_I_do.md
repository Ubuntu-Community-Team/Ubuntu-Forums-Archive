---
title: "Failed Fsck, what do I do?"
date: 2008-12-23
forum: General Help
---

### Post by Angry_Mushi on 2008-12-23
Today, while booting Intrepid Ibex it gave me a "exit 4 failed" or something of the style, I checked for similar errors on the forum but the only one that had gotten any response was for a hardy heron, is there any difference in the procedure to fix an intrepid ibex?

---

### Post by p_quarles on 2008-12-23
> **Angry_Mushi said:**
> Today, while booting Intrepid Ibex it gave me a "exit 4 failed" or something of the style, I checked for similar errors on the forum but the only one that had gotten any response was for a hardy heron, is there any difference in the procedure to fix an intrepid ibex?
It's the same procedure for any distro. Basically, you'll need to boot into recovery mode this time, and when you get the message asking to run the filesystem check manually, run:
```
e2fsck -y /dev/sda1
```
The exact command may vary depending on the name of the partition that needs attention.

---

### Post by Feivel on 2008-12-23
> **p_quarles said:**
> It's the same procedure for any distro. Basically, you'll need to boot into recovery mode this time, and when you get the message asking to run the filesystem check manually, run:
```
e2fsck -y /dev/sda1
```
The exact command may vary depending on the name of the partition that needs attention.

I ran mount | grep ' on / ' and the response was 

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)

Is that entire phrase my boot device?

---

### Post by Angry_Mushi on 2008-12-26
I ran e2fsck and it asked me if I wanted to "clone" blocked areas. I said yes and this morning it started ok, but said I should switch user... is that normal?

---

