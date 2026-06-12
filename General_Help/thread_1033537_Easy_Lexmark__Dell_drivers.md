---
title: "Easy Lexmark / Dell drivers"
date: 2009-01-07
forum: General Help
---

### Post by NoBugs! on 2009-01-07
There are 2 Linux drivers for Lexmark (and dell) printers that can be installed in a few minutes:

Lexmark z700: [http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)
Just get the 2 driver .rpm files:
[http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm](http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm)
[http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm](http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm)

Then go to that directory in the terminal:
```
cd ~/thefolderitisin
ls *.rpm
```
now you should see the driver files.

Then make an installable .deb from those files:
```
sudo alien -d z700llpddk-2.0-1.i386.rpm
sudo alien -d lexmark-z700-cups-driver-1.1.1-1.i586.rpm
```
Notice that in the folder there are 2 new .deb files that can be installed by double clicking on them.


If this doesn't work with your model, the [z600 driver]("http://ubuntuforums.org/showthread.php?t=49714") will more likely work.

---

