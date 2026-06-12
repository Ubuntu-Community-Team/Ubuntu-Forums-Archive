---
title: "K3b and 2nd drive"
date: 2006-03-19
forum: Desktop Environments
---

### Post by evilc on 2006-03-19
I have installed K3b and can see Home & Root folders but can't see my 2nd HD (drive2). In Nautilus it shows up? How do I set it to be seen.
Thanks

---

### Post by Ramses de Norre on 2006-03-19
Can't you acces it through the mountpoint? Every mounted device should have a mountpoint under root.

---

### Post by evilc on 2006-03-19
[QUOTE=Ramses de Norre]Can't you acces it through the mountpoint? Every mounted device should have a mountpoint under root.[/QUOTE]

Not sure what you mean (i'm newb) think I did here's my fstab
TIA

---

### Post by GeneralZod on 2006-03-19
According to your fstab, it should be visible in /media/drive2

Ideally, you should be able to type media:/ in the location bar, but for some reason K3B doesn't support this.

---

### Post by evilc on 2006-03-19
[QUOTE=GeneralZod]According to your fstab, it should be visible in /media/drive2

Ideally, you should be able to type media:/ in the location bar, but for some reason K3B doesn't support this.[/QUOTE]

Thanks for that just checked it does pick it up,

---

