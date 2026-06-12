---
title: "Synaptic package Manager"
date: 2009-05-25
forum: General Help
---

### Post by maitrayei on 2009-05-25
I was installing Java from the terminal and it stopped in between due to power supply interruption. Now when I fo to the 'Synaptic Package Manager', it says that there is another apt-get running and I need to shut it down first. Have tried to restart the PC but no joy after that too.

Anybody has any ideas...

---

### Post by taurus on 2009-05-25
See which process it is.

```
ps -A
```

---

### Post by jawerx on 2009-05-25
killall apt-get. won't this work?

---

### Post by internalkernel on 2009-05-25
Sounds like there is a lock file that synaptic uses, probably left over from the interruption... 

Off the top of my head, i can't remember where it is... maybe /var/cache/apt

---

### Post by kb9tua on 2009-05-25
> **maitrayei said:**
> I was installing Java from the terminal and it stopped in between due to power supply interruption. Now when I fo to the 'Synaptic Package Manager', it says that there is another apt-get running and I need to shut it down first. Have tried to restart the PC but no joy after that too.

Anybody has any ideas...
open a terminal window.
type the word "top" (without the quotes).
look for the process "apt-get" and write down the process number associated with it.
type the letter "k" (without the quotes).
type in the process number and hit enter twice.
this same idea should kill any errent processes that you need to kill.

---

