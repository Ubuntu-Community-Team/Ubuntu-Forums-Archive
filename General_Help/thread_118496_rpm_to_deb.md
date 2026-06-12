---
title: "rpm to deb"
date: 2006-01-17
forum: General Help
---

### Post by brakmaren on 2006-01-17
Hi
I read some where in this forum about a prog in repositorys that could convert a rpm to a deb.
But my memory is not what it's supposed to be :-o
Any one got a name for me ?

---

### Post by 23meg on 2006-01-17
It's called alien.```
sudo apt-get install alien
```

---

### Post by public_void on 2006-01-17
To use (by default it makes a .deb without -d, but I find its best to include it)
```
alien -d /Dir/fileName.rpm
```

---

### Post by brakmaren on 2006-01-17
Muchos gracias compadres :)

---

