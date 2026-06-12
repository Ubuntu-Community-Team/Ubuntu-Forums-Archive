---
title: "Wine for Kubuntu?"
date: 2009-05-15
forum: General Help
---

### Post by dragonbeast25 on 2009-05-15
Cant find anywhere to download wine for kubuntu or how to install it. Thanks.

---

### Post by radiocognition on 2009-05-15
Have you tried,
```
 sudo aptitude install wine 
```

It worked for me

---

### Post by Kareeser on 2009-05-15
Like **radiocognition** said, wine isn't dependent on GNOME or KDE. Installing "wine" from the package repositories will do just fine.

---

### Post by lessgov2007 on 2009-05-16
Yeah, I just installed it via sudo apt-get install wine

Works like magic!

---

### Post by dragonbeast25 on 2009-05-16
It couldn't find wine btw what's best Linux I'd gaming for gaming

---

### Post by dragonbeast25 on 2009-05-16
what is the best linux gaming OS , and how do install wine on kubuntu?

---

### Post by divague on 2009-05-16
Open a terminal terminal and type:

```
$sudo kate /etc/apt/sources.list
```

at the end of that file add this line

```
deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
```

save it, close it and the in the terminal type:

```
$wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
$sudo apt-get update
$sudo apt-get install wine
```

---

### Post by Marlonsm on 2009-05-16
> **dragonbeast25 said:**
> what is the best linux gaming OS , and how do install wine on kubuntu?

If you want gaming, just dual boot Windows and use Linux for everything else (like I do).

---

