---
title: "Mounting a Canon camera in Xubuntu"
date: 2006-09-16
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-16
I've read the threads here about similar issues, but none could help me.

I have a Canon PowerShot A95 I want to mount under Xubuntu.

When I plug it in, nothing happens. No icons on the desktop, no link in the file manager, no nothing.

Should I change my fstab? Should I give up? I don't even know where I should start looking for a way...

Any help?

Gabriel

---

### Post by awong42 on 2006-10-21
I am having the same problem.
Nothing happens, I have a Canon IXUS60.
Someone Please?

---

### Post by taurus on 2006-10-21
Open a terminal and see what dmesg says...

```
dmesg | tail
```
If it sees your USB device as /dev/sdb1, then try to mount it as

```

sudo mkdir /mnt/USB
sudo mount /dev/sdb1 /mnt/USB

```

---

