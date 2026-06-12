---
title: "Drives randomly not being recognized"
date: 2008-12-04
forum: General Help
---

### Post by keygiwawah on 2008-12-04
Sometimes when I boot my computer It doesn't recognize a drive... It does this with all of the drrives, even my hard drive sometimes will not be recognized.  This only happens when I boot ubuntu, not when I boot windows.  So I would think that it's a problem with my ubuntu not my computer.  I was going to reinstall it, but I wanted to see if anyone had any ideas before I did that.

---

### Post by taurus on 2008-12-04
When Ubuntu doesn't recognize your drives during boot, what is the exact error message?

Next time when you are able to boot Ubuntu, post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by drs305 on 2008-12-04
I know you say it occasionally happens with all your drives, but could you tell us whether these are internal drives, external drives, usb drives, etc? Are the drives/partitions listed in fstab?

Are you sure they are not mounting? Is it possible they are mounting to different locations than what you expect? You can run the 'mount' command to see what drives/partitions are mounted.

Although removable drives are not by default entered into fstab, it might provide a bit more reliability.

If you could provide a bit more detail or give us some examples it may help us determine a remedy. Providing the contents of fstab and 'sudo blkid' may also help.

---

### Post by keygiwawah on 2008-12-10
I found the problem... sort of.  For some reason not all of my drive ports work, if I use the ones that work i'm fine.

---

