---
title: "Wall command"
date: 2009-01-02
forum: General Help
---

### Post by bigman1052 on 2009-01-02
Don't know why I cant use the "wall" command on my ubuntu server (i'm pretty new to linux).  Do I need to install a package?

---

### Post by Tomatz on 2009-01-02
In a terminal (at the command line) type:

```
man wall
```

;)

---

### Post by zx5000 on 2009-07-24
Syntax differences ubuntu is the odd duck.
unix & redhat systems

wall message

ubuntu
wall file

try 
echo message | wall

---

### Post by ericosuave on 2009-08-26
echo "message" | wall

---

### Post by sdpagent on 2012-08-15
Does seem odd that ubuntu doesn't use the same methodology as centos which is far easier where you can just type something like ```
wall "my message here"
```

---

