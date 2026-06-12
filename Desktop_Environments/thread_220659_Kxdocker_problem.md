---
title: "Kxdocker problem"
date: 2006-07-21
forum: Desktop Environments
---

### Post by blanc11 on 2006-07-21
Hey guys, I extracted my kxdocker.tar.bx2 

and entered 
```
./configure
```

then it came up with this error message

```
checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!


```

Any help will be appreciated!

---

### Post by taurus on 2006-07-21
You need to install qt-dev, just as the error message said!  So, fire up synaptic and install the development package for qt before you can compile or build kxdocker...

---

### Post by blanc11 on 2006-07-21
Thanks!

Now I get this problem

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```

---

### Post by Freddy on 2006-07-21
This time you need "kdebase-dev"   /// Freddan

---

