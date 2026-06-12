---
title: "kxdocker package ?"
date: 2006-05-05
forum: Desktop Environments
---

### Post by neokod on 2006-05-05
Hi,

There is kxdocker package into the officiels repositories but it's in version 0.34
The current version is 1.1.4a and support XGL/Compiz ..

Is any guru in ubuntu can make a debian package for the new version please ?
I don't see any repositories in apt-get.org for this new version.

I have try to compile, but I have somes problems :
(i'm under dapper/gnome)
```

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```
But I haven't give any parameters to the ./configure !

And I have the libqt3-mt libqt3-headers libqt3-mt-dev packages.. 

If a guru is here.. Thanks

EDIT: For compiling it successfully, this require kdelibs-dev, this works now. But a debian package will be really usefull ! :)

---

