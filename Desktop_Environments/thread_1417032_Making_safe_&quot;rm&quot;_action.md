---
title: "Making safe &quot;rm&quot; action?"
date: 2010-02-26
forum: Desktop Environments
---

### Post by knurledflanges on 2010-02-26
Hello,
I want a way to be able to delete large files on my external hd in Thunar without the system copying them to the internal drive's trash first. I made a custom action in Thunar of:
```
rm %F
```
and that works, but is there a way I can add some kind of safeguard against misclicks, like maybe some way to have the -i option in there and have a terminal pop up? Or does anyone know of a program or some kind of Xfce add-on that does this? Or a way of setting Xfce to just not use trash for files off a certain device? Thanks

---

### Post by aarons6 on 2010-02-26
think if you hold the shift down it deletes files without moving them to the trash.

---

### Post by theozzlives on 2010-02-26
Hit Alt+F2, type in:
```
gconf-editor
```
go to apps > Nautilus > Preferances and check "enable delete"




Oh, just noticed you're not using GNOME... *Never mind*

---

### Post by knurledflanges on 2010-02-26
> **aarons6 said:**
> think if you hold the shift down it deletes files without moving them to the trash.

excellent, thanks!

---

### Post by d3v1150m471c on 2010-02-27
Correct me if I am wrong but I think rm circumvents the trash process.

---

