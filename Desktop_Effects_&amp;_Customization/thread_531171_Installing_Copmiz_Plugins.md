---
title: "Installing Copmiz Plugins"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by wjscott on 2007-08-21
Apologies if this is posted elsewhere - however I have so far been unable to source any mention.

How does one go about installing plugins for compiz? I've taken a snapshot from gtiweb.opencompositing.org and so now have a .tar.gz with the relevant files contained. There's probably a blindingly obvious next step, but it is not one that I have been able to ascertain - any clues please?

Thanks

---

### Post by hyperair on 2007-08-21
First of all, install all the compiz build dependencies, and also make sure you have the packages required to compile.
```
sudo apt-get build-dep compiz
sudo apt-get install build-essentials
```

Once done, you may proceed to compile each and every plugin for Compiz. Basically, what is needed is that you enter each directory:
```
cd /path/to/plugin
```

And then you compile:
```

./configure --disable-kde --prefix=/usr/local
make
sudo make install

```

---

