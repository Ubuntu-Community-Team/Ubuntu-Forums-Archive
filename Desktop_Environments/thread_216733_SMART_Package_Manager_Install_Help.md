---
title: "SMART Package Manager Install Help"
date: 2006-07-15
forum: Desktop Environments
---

### Post by visvak on 2006-07-15
I've just installed SMART package manager from teh repos through synaptic and i love it. very effecient and fast, works with RPMs and has a lot of features SYnaptic dosent have.

but i have a prob, i cna only start with full previlges by using 

```
sudo smart --gui
```

so if i make a menu shortcut, is there anyway i can start it in full previliges, it seems that u cant put "sudo" in the menu shortcut's command

---

### Post by VirtuAlex on 2006-07-16
Check how your synaptic is being started and do the same.

---

### Post by visvak on 2006-07-16
my synaptic goes like usr/bin/synaptic or somethin like dat. but i dont kno the exact location of the SMART thingy.

if i put a gksu or a sudo in the begining like for synaptic, the shortcut dosent work anymore

---

### Post by VirtuAlex on 2006-07-16
> **visvak said:**
> my synaptic goes like usr/bin/synaptic or somethin like dat. but i dont kno the exact location of the SMART thingy.

if i put a gksu or a sudo in the begining like for synaptic, the shortcut dosent work anymore

Actually if you'll run alacarte menu editor you'll se that synaptic is being loaded by
```
gksu /usr/sbin/synaptic
```
Just use quotes around, otherwise gksu takes over --gui option and exits with error since it does not understand it```
gksu "smart --gui"
```

---

### Post by visvak on 2006-07-18
thanks mate. the quotes were the solution.

---

