---
title: "How to tell Ubuntu from Ubuntu 2D using Terminal Commands Only?"
date: 2013-09-26
forum: Desktop Environments
---

### Post by Petro Dawg on 2013-09-26
Hopefully this is a question with a simple answer...

I'm trying to think of a terminal command that will allow me tell if I'm logged in to Ubuntu or Ubuntu 2D. 

I tried...

```
lsb_release -a
``` 

and 

```
uname -a
```

but they appear to both return identical results in both Ubuntu and Ubuntu 2D.

Is there a simple command that has a different output depending on which environment I'm logged into?

Thanks.

---

### Post by Bashing-om on 2013-09-26
Petro Dawg; Hey ...

this:
```

echo $DESKTOP_SESSION

```
output:
12.04 3D =>ubuntu3d is reported
12.04 2D =>ubuntu2d is reported

[INDENT][INDENT]hope that helps
[/INDENT][/INDENT]

---

### Post by Petro Dawg on 2013-09-26
Excellent, works like a charm.

Thank you very much.

---

### Post by Bashing-om on 2013-09-26
Petro Dawg; quite welcome !

Ain't ubuntu wonderful, where there is a will there is a way.

---

