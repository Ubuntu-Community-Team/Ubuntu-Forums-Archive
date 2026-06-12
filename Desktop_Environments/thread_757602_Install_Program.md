---
title: "Install Program"
date: 2008-04-17
forum: Desktop Environments
---

### Post by engjamal99 on 2008-04-17
**[SIZE="6"]i new to linux [/SIZE]**
[SIZE="4"]i download  XCHM Program From Ubuntu web side But i dont know how to install it i try [ sudo apt-get install xchem ]but give message package not found can any one help[/SIZE]

---

### Post by ibutho on 2008-04-17
Enable all your software repositories in /etc/apt/sources.list by uncommenting the universe and multiverse sections (or do this from Add/Remove Programs or Synaptic). After that update your sources by doing "sudo aptitude update" and then install xchm by doing "sudo aptitude install xchm". Alternatively you can use the GUIs tools if you wish.

---

### Post by lizzard on 2008-04-17
Looks like a typo: it's xchm NOT xchem

```
sudo aptitude install xchm 
```

---

### Post by daengbo on 2008-04-17
Or you can just go to Applications > Add/Remove and search for "chm"
You will see viewers for Gnome and KDE.

---

