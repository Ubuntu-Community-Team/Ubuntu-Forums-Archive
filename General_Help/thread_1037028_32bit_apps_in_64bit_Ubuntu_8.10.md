---
title: "32bit apps in 64bit Ubuntu 8.10?"
date: 2009-01-11
forum: General Help
---

### Post by crazyfuturamanoob on 2009-01-11
I have encountered plenty of situations when I got a 32bit app, which I need.

But any 32bit apps don't work on my amd64 version of Ubuntu.

Maybe there are emulators for this? Why 32bit apps don't work?

---

### Post by oldos2er on 2009-01-11
Do you have ia32libs installed?

---

### Post by jocko on 2009-01-11
64 bit Ubuntu can run 32 bit apps. You just have to install 32 bit versions of the libraries the app depends on. Some things are covered by the package ia32-libs, so:```

sudo apt-get install ia32-libs
```
Other dependencies can be solved by a program called [getlibs]("http://ubuntuforums.org/showthread.php?t=474790").

---

### Post by crazyfuturamanoob on 2009-01-12
I got ia32-libs but when I try to install a deb package, he says "error: wrong architecture 'i386'".

But that deb didn't refuse with a 32bit version of Ubuntu.

---

