---
title: "cant install program"
date: 2009-04-15
forum: General Help
---

### Post by chipmunkproof on 2009-04-15
I am trying to install pspshrink. It all goes well, with './configure', and 'make' untill i try to do 'make install'.




adam@adam-laptop ~/Desktop/pspshrink-1.1.1 $ make install
make[1]: Entering directory `/home/adam/Desktop/pspshrink-1.1.1'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'pspshrink' '/usr/local/bin/pspshrink'
/usr/bin/install: cannot create regular file `/usr/local/bin/pspshrink': Permission denied
make[1]: *** [install-binPROGRAMS] Error 1
make[1]: Leaving directory `/home/adam/Desktop/pspshrink-1.1.1'
make: *** [install-am] Error 2

Any help would be greatly appreciated.
Adam

---

### Post by Nero147 on 2009-04-15
You need to run
sudo make install
also make sure that when you run make you do 
sudo make

---

### Post by chipmunkproof on 2009-04-15
well that was easy hahaha
thanks alot brother
Adam

---

