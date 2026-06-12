---
title: "Great text editor - need a deb"
date: 2006-07-28
forum: Desktop Environments
---

### Post by saracen on 2006-07-28
Does anyone have a .deb for [scribes]("http://scribes.sourceforge.net/")  I want to install it but the setup script is in python and there doesn't seem to be a clean way to uninstall it.

---

### Post by asplode on 2006-07-28
Well, if the script to install it is

```
make install
```

than the script to make it go byebye would be
```

make uninstall
```

---

### Post by OffHand on 2006-07-28
```
sudo apt-get install checkinstall
```

then the last step of install will be:

```
sudo checkinstall
```

That way you can remove it using Synaptic

---

### Post by saracen on 2006-07-28
it's not make... it's a python install script.  So the way to install it is ```
python setup.py install
```.  There is no uninstall option - hence the deb

---

### Post by kacike on 2007-06-10
You can get scribes at [www.getdeb.net]("http://www.getdeb.net")

---

### Post by gjtoth on 2007-06-10
or... you can get it via Synaptic.

---

