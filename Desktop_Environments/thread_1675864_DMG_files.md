---
title: "DMG files"
date: 2011-01-26
forum: Desktop Environments
---

### Post by smss on 2011-01-26
Hi.
How to open .dmg files?

---

### Post by Grenage on 2011-01-26
> **smss said:**
> Hi.
How to open .dmg files?

[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

---

### Post by smss on 2011-01-26
Ok.
But I did not understanded it!

---

### Post by Grenage on 2011-01-26
First you might need to make a mount point:

```
sudo mkdir /media/dmg
```

Then mount it; you'll need to replace the paths with whatever you have:

```
sudo mount -t hfs -o loop */home/smss/myImage.dmg* */media/dmg*
```

I've never done this before, but I imagine that would work.

---

### Post by smss on 2011-01-27
> **Grenage said:**
> First you might need to make a mount point:

```
sudo mkdir /media/dmg
```Then mount it; you'll need to replace the paths with whatever you have:

```
sudo mount -t hfs -o loop */home/smss/myImage.dmg* */media/dmg*
```I've never done this before, but I imagine that would work.

Thank you very much.

---

