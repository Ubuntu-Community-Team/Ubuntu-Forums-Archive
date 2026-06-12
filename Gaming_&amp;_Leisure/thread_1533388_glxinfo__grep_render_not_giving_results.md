---
title: "glxinfo | grep render not giving results"
date: 2010-07-17
forum: Gaming &amp; Leisure
---

### Post by bigdumbapple on 2010-07-17
Every time I enter the code:
```
glxinfo | grep render
```I receive no output. It says neither yes, nor no. It just moves on to alexander@alexander-desktop:~$ again.  Can I get some help?

---

### Post by Perfect Storm on 2010-07-17
```
lspci |grep VGA

glxinfo | grep direct

```

---

### Post by hikaricore on 2010-07-18
A simple:

**glxinfo**

Might actually help show what the problem is.
If the output is non-standard because something is wrong, it may not show the Direct Rendering line at all, thus returning no info.

---

