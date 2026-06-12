---
title: "Step compile problem"
date: 2007-12-17
forum: Education &amp; Science
---

### Post by smarion on 2007-12-17
Hi,
I'm in desperate need of help.

I've been unsuccessfully trying to compile Step on my PC.
[http://edu.kde.org/step/obtain.php](http://edu.kde.org/step/obtain.php)

I get this error in the compile process:
```
cmake -DCMAKE_INSTALL_PREFIX=$KDEDIRS ..
CMake Error: ERROR: Could not find KDE4 kde4-config
-- Configuring done

```

I presume that the problem is because I can't find the right KDE library and gmm. I tried to install kdebase-dev-kde4 but I get an error with the kdebase-runtime-bin-kde4 package.

Any help would be appreciated. :-)

---

### Post by lustefaniak on 2008-01-13
use 
```
export PATH=$PATH:/usr/lib/kde4/bin
```
and then try to compile

---

### Post by smarion on 2008-01-13
Thanks for the reply!

I menaged to overcome that problem and a few more on the way.

Now, I'm getting the following error following make:
```

/usr/bin/ld: cannot find -lphonon
collect2: ld returned 1 exit status
make[2]: *** [step/step] Error 1
make[1]: *** [step/CMakeFiles/step.dir/all] Error 2
make: *** [all] Error 2

```

---

### Post by lustefaniak on 2008-01-13
you need to install libphonon-dev.
also installing kde4-devel should fix your build env

---

### Post by smarion on 2008-01-13
Works now.

Forgot about the devel package... Thanks!

---

