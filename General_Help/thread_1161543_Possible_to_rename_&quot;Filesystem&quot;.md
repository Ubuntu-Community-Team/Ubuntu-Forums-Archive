---
title: "Possible to rename &quot;Filesystem&quot;?"
date: 2009-05-16
forum: General Help
---

### Post by Fzang on 2009-05-16
"Filesystem" is simply / so there must be some way to rename it? I doubt it would harm the system as everything looks for / and not "filesystem"

Any way to rename somehow?

---

### Post by taurus on 2009-05-16
Are you talking about volume label?

---

### Post by Rocket2DMn on 2009-05-16
"Filesystem" is a name given by Nautilus.  I suppose it would be possible to put a label on your root partition, though I'm not sure what benefit that would be, or if nautilus would even show it.  If you wanted to try, you would need to do it from a LiveCD since you can't change the label on a mounted partition.  You would use the "e2label" command, like:
```
sudo e2label /dev/sda1 SystemRoot
```
where sda1 is the root partition, and SystemRoot is the label you want to use.

---

### Post by CatKiller on 2009-05-16
> **Fzang said:**
> Any way to rename somehow?

You could right-click on it and select Rename...

---

### Post by Fzang on 2009-05-17
I tried renaming in Nautilus and it gives me the error 

"Sorry, could not rename "Filesystem" to "Ubuntu Disk": Operation not supported by backend"

---

### Post by CatKiller on 2009-05-17
Ah. I saw the option was there, but didn't try it. I'd imagine that the "Filesystem" link is a .desktop file stored somewhere, but I haven't been able to locate it yet.

---

### Post by Ericyzfr1 on 2009-05-17
I believe you can try to change it with Gparted Live CD, but it may not work ...I have never tried it. I know that in Gparted you can rename a disk or partition after unmounting them and the changes will only show after a system re-start.

---

