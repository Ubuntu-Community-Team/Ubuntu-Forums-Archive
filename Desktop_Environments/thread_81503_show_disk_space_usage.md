---
title: "show disk space usage"
date: 2005-10-24
forum: Desktop Environments
---

### Post by fizgig on 2005-10-24
Is there an app that shows you how your disk space is being used?  I'd like to know where my disk space went!

---

### Post by Kyral on 2005-10-24
System Tools -> System Monitor

or

```
df -h
```

On the commandline

---

### Post by signbarn on 2005-10-24
You can use the system monitor to get a graphical display of your disk usage. It's the last tab.

---

### Post by fizgig on 2005-10-24
Thanks for the tip.  When I click the last tab the app appears to freeze and I don't see any results.  Kind of weird.

---

### Post by ranf on 2005-10-24
```
du ~ | less
```
shows disk usage of every subdir in your home.

---

