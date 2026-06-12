---
title: "QT errors on ./configure"
date: 2005-08-04
forum: Desktop Environments
---

### Post by toran on 2005-08-04
I'm trying to install kmuddy ([http://kmuddy.net](http://kmuddy.net)) from source (there is no ubuntu package), and I am running into the following error on "./configure":

```
checking for Qt... configure: error: Qt (>= Qt 3.1.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
``` 

What do I need to install to fix this problem? I have all the libqt related packages I can installed.

Please help me.

thanks!

---

### Post by SGC on 2005-08-04
**If you have the following packages, you can compile any KDE/QT based program without any problem:**
libqt3-headers
libqt3-mt-dev
libqte-mt3                           [universe repository]
libqte-mt3-dev                    [universe repository]
kdelibs4-dev
libqt3-compat-headers       [not sure about this one]

---

### Post by toran on 2005-08-04
I have all of the above installed, and I am still getting the error.

---

### Post by SGC on 2005-08-04
[QUOTE=toran]I have all of the above installed, and I am still getting the error.[/QUOTE]
 I can't think of any other packages except **kdebase-dev**

---

### Post by Roptaty on 2005-08-04
Try running configure with --with-qtdir.
```

./configure --with-qtdir=/usr/share/qt3

```

---

### Post by lognok on 2005-09-06
Hi every one, had a similar problem, installing SpeedCrunch, which is designed for KDE, on GNOME. Had all the dependencies, but it wouldn't install, kept saying I should check my qt 3.2 dependency, when I had all libqt's installed.
   Then I checked the conf.log it creates and it said that is was missing G++. Installed that and configured the program with no problem.
   I hope that this can help in any small way possible, knowing it's not the same program. If not, then I hope you solve/solved your problem. :-|

---

