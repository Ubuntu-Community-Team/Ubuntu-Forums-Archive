---
title: "NWN custom portraits displaying as blank boxes"
date: 2007-04-10
forum: Gaming &amp; Leisure
---

### Post by cjl2301 on 2007-04-10
Thanks to the great install script I found on these forums, I have NWN up and running on my Edgy box.

However, for some reason the custom portrait files that worked under windows only display as blank, white boxes on my linux install.

I've checked the format and they are uncompresses tgas as needed.  Since they work in Windows, I don't think there is an issue with the portrait files themselves.  Although, maybe there is because one of them actually does show up correctly.

Has anyone else run into this?  I tried opening them and resaving with GIMP and it didn't help.  Perhaps another image editor might work?

---

### Post by Perfect Storm on 2007-04-10
1. Make sure the fole name on each of every portrait doesn't contain captial letters, if they do rename them.
2. No spaces ofcause.

---

### Post by cjl2301 on 2007-04-11
> **Artificial Intelligence said:**
> 1. Make sure the fole name on each of every portrait doesn't contain captial letters, if they do rename them.
2. No spaces ofcause.

Well I'll be - sure enough it was the capital letters!   You are a genius!  Thanks!

---

### Post by arron on 2008-12-19
Sweet, ive been bothered by this for years now....

this fixes it for me, quick way to run it in your portraits directory:

```

for i in *; do mv $i `echo $i | tr [:upper:] [:lower:]`; done

```

Thanks!

---

