---
title: "adding in sources.list"
date: 2009-01-10
forum: Desktop Environments
---

### Post by num on 2009-01-10
Hello,

I am trying to add the following line in sources.list:

```
deb http://kanotix.com/files/debian/ ./
```

but it doesn't allow me to save and tells me I do not have the permission to do so. How can I add that line into sources.list?

---

### Post by blackened on 2009-01-10
In the terminal use

```
gksudo gedit /etc/apt/sources.list
```

then edit the file accordingly and save.

---

### Post by cdtech on 2009-01-10
In a terminal use:
```
sudo gedit /etc/apt/sources.list
```

**UPDATE::.**
Sorry blackened I was a little slow, lol

---

### Post by num on 2009-01-10
thanks i will try this and report.

---

