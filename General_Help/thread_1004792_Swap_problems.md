---
title: "Swap problems"
date: 2008-12-07
forum: General Help
---

### Post by Sjeti on 2008-12-07
I installed Slackware on another partition and selected it to share the same swap, but after installing it my Ubuntu partition isn't using the swap any more.

First off can you share swaps? I see no reason why you can't...

And if you can share them, where on ubuntu can you specify your swap partition?  i.e. what .config or .list or whatever to I need to edit to get it working again.

---

### Post by taurus on 2008-12-07
Yes, you can use the same swap partition with other Linux distros.  When you installed Slackware, it probably reformatted your swap partition so it has a new UUID now.  Therefore, you need to change it in /etc/fstab (under Ubuntu).

```
free
cat /etc/fstab
sudo blkid

```

---

### Post by Sjeti on 2008-12-07
Yup, my UUID's were mismatched.

I just went in and copied the UUID into fstab, it should load when I reboot.

---

### Post by scragar on 2008-12-07
first, I'd see if it's in use:
```
mount | grep swap
```
if it's not in use try it, first find the partition:
```
sudo fdisk -l | grep swap
```
And then try to swap it on manualy:
```
sudo swapon **/dev/sda5**
```
if that works let me know, and I'll help you add it to the fstab, so it's done automaticly.

---

### Post by Sjeti on 2008-12-07
I knew the swap wasn't working because it wasn't showing up in conky.

The swapon command worked though, thanks.

---

### Post by taurus on 2008-12-07
No need to reboot.  Just run

```
sudo mount -a
```

---

