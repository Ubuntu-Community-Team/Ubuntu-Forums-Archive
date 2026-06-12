---
title: "How to install c compiler on ubuntu"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by Jagdeep on 2007-04-21
[COLOR="RoyalBlue"][B]Hey guys, I'm facing problems while installing gcc on linux.
Can anybody help me.[/B][/COLOR]

---

### Post by hikaricore on 2007-04-21
I believe that:

```
sudo aptitude install build-essential
```

Should install nearly everything you need, but aside from that what seems to be the trouble?

---

### Post by Swarms on 2007-04-22
> **hikaricore said:**
> I believe that:

```
sudo aptitude install build-essential
```

Should install nearly everything you need, but aside from that what seems to be the trouble?

To use this thread, I've got a .tar.gz file, and it is supposed to be compiled into a program, installed your packages, what is next step?

---

### Post by lakersforce on 2007-04-22
This thread should be moved to the appropiate section.

---

### Post by hikaricore on 2007-04-22
> **Swarms said:**
> To use this thread, I've got a .tar.gz file, and it is supposed to be compiled into a program, installed your packages, what is next step?

Depends alot on the program, but you'll need to extract the files first

```
tar -xzfv filename.tar.gz
```

Then **cd** into the directory of the code. (this is where the v flag in the tar command comes in handy as it extracts in verbose mode)

the usual procedure is:

```

./configure
make
sudo make install

```

Sometimes there is no configure file and source uses autogen, you can usually find more info from the website you got the software from.

---

