---
title: "How to find out the name of source package given shared library"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Roobert on 2006-09-15
I know there must be an apt command for this....but how do I find out the name of the package I should install if all I know if one of the libraries that pack with it? 

Example: I need libXm.so.3 to run a particular program, but I have no idea what package/program it belongs to in Synaptic.

---

### Post by lamego on 2006-09-15
Go to:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
And use the "Search the contents of packages" search section.

---

### Post by mitch.c on 2006-09-15
You could also install apt-file:
```
sudo apt-get install apt-file
sudo apt-file update
apt-file search libXm.so.3
```

---

### Post by Roobert on 2006-09-18
Thanks! Apt-file was what I was looking for.

Cheers,

~R.

---

