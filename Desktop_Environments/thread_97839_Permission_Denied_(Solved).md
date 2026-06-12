---
title: "Permission Denied (Solved)"
date: 2005-12-01
forum: Desktop Environments
---

### Post by karmon on 2005-12-01
hey, i'm trying to install a couple of toolchains, but whenever i try i get Permission Denied. i know this is because i have to be in the root terminal, but in Ubuntu 5.10 (which is what im on right now), there doesn't seem to be a root terminal.

---

### Post by seismicmike on 2005-12-01
You can run any commands that need to be root from a normal terminal by using the keyword "sudo"
```
sudo <your commands>
```
You will then be prompted for your password

Alternatively, if you type
```
sudo -s
```

You will be changed into root mode and everything you do will be as root.

Hope I helped :)

---

### Post by karmon on 2005-12-01
thanks alot, the first sudo <commands> idea i tried earlier, and it didnt work, but sudo -s worked like a charm :) .

---

