---
title: "Wubi to full install"
date: 2009-01-19
forum: General Help
---

### Post by trixman on 2009-01-19
if i want to go to a full install without using the LVPM way. i am unsure on how to partition my hard disk.  would it be easier to place the cd in of 8.04 at the boot of the pc and start over.

totally newbie

:KS

---

### Post by Feivel on 2009-01-19
that's what I did only I added another 320 gig HD to do so. Only before I did I ran the command

```
dpkg --get-selections > installed-software
```

and after reinstall of Ubuntu I ran

```
dpkg --set-selections < installed-software
```

then

```
dselect
```

Went and made some lunch then came back to a fresh install of Ubuntu with every program I had installed on my Wubi install.

---

### Post by trixman on 2009-01-19
i ran a fresh install, i saved all my  pictures to a usb flash. and got rid of windows totally.

thanks  guys
:KS

---

### Post by Feivel on 2009-01-19
> **trixman said:**
> i ran a fresh install, i saved all my  pictures to a usb flash. and got rid of windows totally.

thanks  guys
:KS

Yeah, I ditched Vista and never felt happier. Kept XP as a duel boot on my laptop but my desktop is free of the Microsloth monster.

---

### Post by trixman on 2009-01-19
i am totally amazed how much better linux ubuntu is than vista.  the one thing that is great with linux that i learned is that it can breath life into older machines and make them workable again.

thanks to all for this great forum

:KS

---

