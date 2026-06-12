---
title: "qt-sdk package missing"
date: 2011-02-13
forum: Desktop Environments
---

### Post by Matpen on 2011-02-13
Hi everyone!

I was trying to setup a cross-platform development environment with qt, an thus looked for the qt-sdk package I used to install on my 32-bit machine.

This package appears to have been deleted from 64-bit ubuntu maverick, but I do not understand the [details]("https://launchpad.net/ubuntu/maverick/amd64/qt-sdk")... :?

- Has this package been renamed, or is there another one in place of it?
- Is this package going to be available again in the future?

Many thanks in advance!

PS: I am aware that one can install the sdk by [downloading]("http://qt.nokia.com/downloads/sdk-linux-x11-64bit-cpp") the installer, but for unattended install I prefer the apt package...

---

### Post by gordintoronto on 2011-02-13
Start Synaptic, and search (not quick search) for qt develop

---

### Post by linuxsyst on 2011-02-13
```
sudo apt-get install libqt4-dev
```
That will install it.

---

### Post by Matpen on 2011-02-13
Unfortunately libqt4-dev refers to the framework itself, not to the sdk. Synaptic lead to the same conclusion...

Aparently, the package qt-sdk has been removed since it is now "arch all" (=architecture all?)... this makes sense, because it is a meta-package.

But how to install it then? Should one grab it from the i386 repository?

Thanks again!

---

### Post by Matpen on 2011-02-16
bump

---

### Post by Matpen on 2011-02-20
bumpity bump

---

### Post by gmargo on 2011-03-06
Bump again.

I just ran into this problem myself.  In Maverick 64-bit, qt-sdk is present in Source form only, not binary.

The apparently related bug report doesn't make sense to me.
[https://bugs.launchpad.net/ubuntu/+source/qt-sdk/+bug/618075](https://bugs.launchpad.net/ubuntu/+source/qt-sdk/+bug/618075)

---

### Post by gmargo on 2011-03-06
Here are the dependencies for qt-sdk; install these packages for the same effect (in 10.10 Maverick 64-bit):

build-essential cmake gdb git-core libqt4-dev libqt4-opengl-dev libphonon-dev qt4-designer qt4-dev-tools qt4-doc qt4-doc-html qt4-qmake qtcreator qtcreator-doc subversion libqtwebkit-dev

---

### Post by Matpen on 2011-03-07
I filed a [question on launchpad]("https://answers.launchpad.net/ubuntu/+source/qt-sdk/+question/147275"). The package maintainers agree that the package should not have been removed, and are working towards restoring it in the repos.

Use gmargo workaround in the meanwhile:
sudo apt-get install build-essential cmake gdb git-core libqt4-dev libqt4-opengl-dev libphonon-dev qt4-designer qt4-dev-tools qt4-doc qt4-doc-html qt4-qmake qtcreator qtcreator-doc subversion libqtwebkit-dev

---

