---
title: "cant install uplink"
date: 2010-12-12
forum: Gaming &amp; Leisure
---

### Post by Kocrachon on 2010-12-12
So on ubuntu 10.10 64 bit I am trying to install a game called uplink and I get the following error..

```
.setup4184: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```Now I tried a few different posts with no success because they have links that don't work anymore because they are 3 years old...

```
http://whynotwiki.com/How_I_installed_N_on_64-bit_Linux

http://ubuntuforums.org/showpost.php?p=1339711&postcount=25


```But now I have made some progress using this link

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

The issue I have run into is when I try to install the libs via the following command I get the following error with it..

```
getlibs -l libgtk-1.2.so.0

The following i386 packages will be installed:
libgtk1.2
Continue [Y/n]? y
E: No packages found
```Anyone able to help me get this game installed? Its the linux version of the game.

---

### Post by Perfect Storm on 2010-12-12
libgtk1.2 is no more. It's obsolete and doesn't get any updates nor security updates either.

Though you can get it from previous ubuntu releaes: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Then use getlibs to install it afterwards.

---

