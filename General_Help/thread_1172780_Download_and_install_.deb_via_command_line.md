---
title: "Download and install .deb via command line"
date: 2009-05-28
forum: General Help
---

### Post by ninjapirate89 on 2009-05-28
Is there a way to download a .deb from a website using the command line and install it?

---

### Post by _Purple_ on 2009-05-28
```
wget  http:url/of/the/deb/file/filename.deb
sudo dpkg -i filename.deb
```

---

### Post by ninjapirate89 on 2009-05-28
Thanks a bunch.

---

### Post by _Purple_ on 2009-05-28
You are welcome. :)

---

### Post by colau on 2009-05-28
> **ninjapirate89 said:**
> Is there a way to download a .deb from a website using the command line and install it?
```

curl http://url/filename.deb
dpkg -i filename.deb

```
Does it work?

---

### Post by shantiq on 2011-06-05
> **_Purple_ said:**
> ```
wget  http:url/of/the/deb/file/filename.deb
sudo dpkg -i filename.deb
```


since the deb usually goes to Downloads


running

```
wget  http:url/of/the/deb/file/filename.deb
cd Downloads
sudo dpkg -i filename.deb
```

is good too :KS

---

### Post by uRock on 2011-06-05
Necromancy

Thread Closed

---

