---
title: "beryl issues"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by giora on 2007-04-24
hi. first of all, i have to admit i'm a newbie, so please be patient with me...
i seem to have a problem with beryl and i can't find a solution for it.
i manged to render my beryl settings useless after to much testing, so i completly removed it with synaptic. after reinstalling it i found out that all the previous settings where saved and are again causing the same problems.
i hope someone could tell where i'm wrong.

 thank you in advacne.

---

### Post by dad311 on 2007-04-24
Try removing the .beryl directory from your home directory.

rm -r /home/username/.beryl

---

### Post by giora on 2007-04-24
thanks dad 311. I tried removing beryl and emerald from my home dir,but still, as soon as I reinstall beryl, my old mistakes(forcing xgl on beryl setting) cause my pc to freeze.

---

### Post by Waappu on 2007-04-24
> **giora said:**
> thanks dad 311. I tried removing beryl and emerald from my home dir,but still, as soon as I reinstall beryl, my old mistakes(forcing xgl on beryl setting) cause my pc to freeze.

Hi

Try this
```
rm ~/.beryl-managerrc
```

---

### Post by giora on 2007-04-26
thank you waappu! took your advice, problem solved...

---

