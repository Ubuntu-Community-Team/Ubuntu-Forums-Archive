---
title: "Install simutrains"
date: 2008-08-15
forum: Gaming &amp; Leisure
---

### Post by timboellis on 2008-08-15
How do I Install simutrains I have tried but failling desperatly is there a deb or an easy way to install not a clue what packages to download

---

### Post by Ozor Mox on 2008-08-15
The Simutrans downloads are usually available from the official forums, but they have been having problems recently and it seems that the last stable version is not available on there.

To make it work though, you need the executable for Linux and a pak. If you download from [this link](http://forum.simutrans.com/index.php?topic=15.0), you'll get a slightly newer version than the last stable. From here you would need to download at least the following:

Linux with SDL and SDL_mixer
pak64 Basis (with or without food/waste chains) **OR** pak128 1.4.3.1 alpha

Pak64 would give you the smaller official graphics set, pak128 would give you the larger and more detailed graphics. There are also other paks available, but these are the two most common.

You need to extract all files to the same directory, and then run the Simutrans executable using

```
./simutrans -nomidi
```

at the command line when you are in the directory, or double clicking the file.

EDIT: It seems that all available files are at the game's [SourceForge page](http://sourceforge.net/projects/simutrans/). 99.17.1 is the last stable version. Basically you need the Linux executable and a pak, and they need to be extracted into the same directory.

---

