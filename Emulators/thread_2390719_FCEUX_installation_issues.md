---
title: "FCEUX installation issues"
date: 2018-05-01
forum: Emulators
---

### Post by JesterDev on 2018-05-01
I followed a guide that was linked here on the official site. Only I downlaoded the latest source as the svn link was no good. 
Installed scoons, installed essential build.

sudo scons INSTALL:

```
...
scons: done reading SConscript files.
scons: Building targets ...
scons: Nothing to be done for `INSTALL'.
scons: done building targets.

```

So seems to me something was built. But I cannot seem to find it, or figure out how to run it. Whereis gfceux results in nothing.

---

### Post by Holger_Gehrke on 2018-05-14
1) fceux is in the repositories in version 2.2.2. Unless you absolutely positively need whatever fixes went into 2.2.3, I wouldn't bother with compiling it myself.

2) 'scons install' just installs the compiled binaries. If there are no binaries compiled yet, there's "Nothing to be done for 'INSTALL'". Run scons (without sudo, without parameters) to compile. scons will check for needed libraries. Unless you already have them installed, you will have to install the '-dev' packages for several libraries; the ones i needed were libgtk2.0-dev and libsdl1.2-dev, but I already have quite a few -dev packages installed, so you might have to install some others additionally. Once scons is happy with the libraries it will call the compiler and after a lot of compiling and linking, there will be binaries in the subdirectory 'bin' of the directory into which you put the code. Change to that directory and try the emulator with './fceux', it should run. If you run 'sudo scons install' now, it will copy the program(s, there also a server for network play) to /usr/local/bin and other files to other places under /usr/local. The gnome-frontend gfceu (not gfceu**x**), while not exactly necessary, can be found in the directory 'gfceu'. It will not be installed by 'scons install', you would have to install it separately, using the 'setup.py' script in the same directory. 'scons install' also installs a desktop file to '/usr/local/share/applications', but there's a problem with this file: it's EXEC-line calls '/usr/bin/fceu' which is not the right path for the compiled program. Either it wouldn't start at all, or  -- if you've got the version from the repositories installed -- it would call the older version. Easy enough to fix, once you know about it ...

Holger

---

