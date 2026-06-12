---
title: "missing dependancies on fyre - libcairo, libpixman"
date: 2005-11-29
forum: Desktop Environments
---

### Post by ginapi on 2005-11-29
Maybe someone could find this usefull :

I tried to install fyre via apt-get on my Breezy.
To have the application working I had to do the following:

As root create a symlink to the new cairo library with the old name of the library, as required from fyre.

```
cd /usr/lib
cp -s libcairo.so.2.2.3 libcairo.so.1 

```

Add the libpixman library, required from fyre. 

```
apt-get install libpixman1
```

Now everything works fine! Have fun with fyre :D

---

