---
title: "how do i compile new programs"
date: 2009-02-23
forum: Desktop Environments
---

### Post by ghostz on 2009-02-23
i want to learn how ot build these programs an anyone give me a tut or how to ?


p.s i dnt know if im posting tin the right place

---

### Post by oldos2er on 2009-02-23
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

 [https://help.ubuntu.com/community/OtherWaysToInstall](https://help.ubuntu.com/community/OtherWaysToInstall)

---

### Post by WatchingThePain on 2009-02-23
Those links are a tutorial dude!

---

### Post by davec64 on 2009-02-23
Download the source, unpack the archive and have a look at the readme file first!
Once you're happy there isn't an installation script or some special steps to compiling, then it should be a simple:

```

cd **to unpacked folder**
./configure
make
sudo make install

```

Make sure you've already installed any required dependancies and if you get an error look for a dependancy you've missed. :)

EDIT:

The first tutorial is spot on!
checkinstall is better as you can then use apt to remove the program later.

---

