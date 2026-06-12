---
title: "Wine"
date: 2006-03-01
forum: Gaming &amp; Leisure
---

### Post by Sommer on 2006-03-01
Hey

Can wine run on a Breezy 64-bit system ??

---

### Post by earobinson on 2006-03-01
I dont see why not
```
sudo apt-get install wine
```

---

### Post by Sommer on 2006-03-01
it make an error.. the wine-pack doent exsist. Maybe iv got to enable something.
I allready enabled univers... hmm

---

### Post by ins on 2006-03-02
did you update?

```
sudo apt-get update
```

---

### Post by Yagisan on 2006-03-02
wine is not avalible on amd64, because of its nature as a **32bit i386 windows** compatablity layer. Ideally you can install it in an i386 chroot (good soloution, but takes a short while to set up), or you can force install the wine .debs on amd64 (not-so-good, it may break your systems, but it seems to work for others.) I use the chroot myself. There should be a howto on either the wiki or the forums for setting up the chroot.

---

