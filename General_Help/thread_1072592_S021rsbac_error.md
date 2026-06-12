---
title: "S021rsbac error"
date: 2009-02-17
forum: General Help
---

### Post by jms1989 on 2009-02-17
Ok, I've search for this here and through google and got nothing. Bascily, when booting ubuntu, I've noticed an error appears on my screen but doesn't stop the boot process.

It goes something like this,

```

/etc/rcS.d/S021rsbac: Unexpected error near token "("

```

I tried looking in my logs but nothing turns up that looks abnormal. If this troublesome program is unneeded, then I'll just delete it from my /etc/rcS.d directory but I need your approval for it. That error line is the best I can get from memory and shows up at every boot.

Any clues of what might help the investigation?

---

### Post by heindsight on 2009-02-21
Try finding out what package that script comes from.

Try doing
```
dpkg -S $(readlink -f /etc/rcS.d/S021rsbac)
```
If that doesn't give the package name then open the file in your favourite text editor to see if that can tell you which package it comes from.

The error you're getting seems to be caused by a coding error in the script, so if you know something about shell scripting you may be able to fix it quite easily. Otherwise you could post the script here and I or someone else could take a stab at figuring out why it gives an error.

EDIT:
The name S021rsbac is a bit strange. Usually rc?d links have only 2 digits between the S/K and the name of the init.d script.

Having done a bit of searching around it looks like that's an init script for RSBAC (Rule Set Based Access Control) which apparently is a
> kernel patch which adds several
 mandatory access models to the Linux kernel. These models can be used to
 enhance the security of a Linux system. 


---

### Post by jms1989 on 2009-02-21
actually I don't have an error from that anymore. I recently did a disk-upgrade to 8.10 for my new computer so no more errors. So far so good.

---

