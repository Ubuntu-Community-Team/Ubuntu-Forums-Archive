---
title: "How to determine what application requests KDE packages?"
date: 2012-10-23
forum: Desktop Environments
---

### Post by Sean Dewlin on 2012-10-23
I got some unwanted applications like Nepomuk Backup or Nepomuk File Indexing Controller and I'd like to remove them. But since they are dependencies, I cannot. Each time I start Software Updater, it installs them again. Seems like one day I have accidentally installed a KDE application. Is there any way to determine it?

---

### Post by jerrrys on 2012-10-23
Any installed package that starts with a "K" is a suspect.  You could right click and check package properties with synaptic package manager.

---

### Post by Sean Dewlin on 2012-10-24
So basically there is no other way? Somehow I got k3b package installed, but I don't use K3b. May another program (CD/DVD burners probably) use k3b package?

---

### Post by Cheesehead on 2012-10-24
Synaptic is a great tool for this purpose.

If you just have a fast question to lookup, the apt-cache depends/rdepends command is also good.

Depends example: Here are the packages nepomuk depends upon:
```
$ apt-cache depends libnepomuk4
libnepomuk4
  Depends: libc6
  Depends: libkdecore5
  Depends: libkdeui5
  Depends: libqt4-dbus
  Depends: libqtcore4
  Depends: libqtgui4
  Depends: libsoprano4
  Depends: libstdc++6
  Breaks: kdelibs5
  Breaks: kdelibs5-data
  Replaces: kdelibs5
  Replaces: kdelibs5-data

```

Reverse-depends example: Here are the packages depend upon k3b:
```
$ apt-cache rdepends k3b
k3b
Reverse Depends:
  kmediafactory
  dvd95
 |uck
  quodlibet-plugins
  ichthux-desktop
  ezgo-multimedia
 |aptoncd
  kubuntu-full
  kubuntu-desktop
  k3b-dbg
  juk

```

---

### Post by bra|10n on 2012-10-24
+1. Apt is brilliant.

---

### Post by Sean Dewlin on 2012-10-25
Simply opening Ubuntu Software Center, then searching for KDE in installed packages and removing them has solved the problem.

---

