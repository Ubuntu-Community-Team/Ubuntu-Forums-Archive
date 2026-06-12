---
title: "Installing a game problem"
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by Ziggyz on 2007-07-14
Ok I am trying to install AA on ubuntu feisty, and when I click ok to write it to usr/local/games/armyops/

It says "No write permission to usr/local/games/" How do I fix this?

---

### Post by hikaricore on 2007-07-14
You need to run the installer with either:

```
gksudo installername
```

Replace "installername" with the actual name of the installer file and you should be good to go.

Files may only be written in certain directories of the file structure with root/fake root (aka sudo) permissions.

---

