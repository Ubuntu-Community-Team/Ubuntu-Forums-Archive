---
title: "Problems with new compiz/ccsm"
date: 2008-03-30
forum: Desktop Effects &amp; Customization
---

### Post by Smatt454 on 2008-03-30
I just downloaded the updates for compiz. I cant get any of the new plugins to work. All of them crash my computer. Whats even worse is it wont let me change the key bindings! I am in serious need of this because some of my keys dont work and i dont have a spare keyboard at hand :(

is there a new way to change the key bindings? or is there at least a way to see  what the current key bindings are


also....
to get the new ccsm working, ihad to comment out this line in /usr/bin/ccsm:
```
idle = ccm.IdleSettingsParser(context)
```

and on the ubuntuforums, to get the new compiz plugins, i was told to use this repository:
```
deb http://kwatrow.nl/repo Gutsy compiz-fusion-git
```

however, when i install compiz from this repository, i get an error when i try to start compiz.

```
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libcrashhandler.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'crashhandler'
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libextrawm.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'extrawm'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libsplash.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'splash'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libbench.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'bench'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libfirepaint.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'firepaint'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libreflex.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'reflex'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libgroup.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'group'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libaddhelper.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'addhelper'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libcubecaps.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'cubecaps'
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libcubereflex.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'cubereflex'
smatt454@kubuntu:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

does anyone think they can help me figure out how to change the key bindings and/or how to get the new plugins.

i would greatly appreciate this.


EDIT:

i am using Kubuntu 7.10 (KDE)
this is my video card ```
VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
```

---

### Post by linuxaz on 2008-03-30
Smatt454,
I could be wrong, but I think the git versions are potential backports?  If so, you very well could have problems.  For the most stability, I suggest only using the official repos for Kbuntu 7.10..

bertman

---

### Post by Smatt454 on 2008-03-30
using the official repos do make compiz work

but the keybinding option is still lost with the latest upgrade

---

