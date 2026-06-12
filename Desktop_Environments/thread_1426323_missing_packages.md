---
title: "missing packages"
date: 2010-03-10
forum: Desktop Environments
---

### Post by halit.yilmaz on 2010-03-10
hi all,

i am really a newbie on ubuntu. When I first begun to use Ubuntu, i tried to use MonoDeveleop and serving .net web applications on apache web server and installed mono tarball it didn't work correctly anyway. 

and i use php for web development, use lazarus for programming. but my problem is after i uninstalled mono deb packages ( during installation mod_mono) some programs on my system are not working. 

f- spot, sysinfo etc. i tried to install missing packages (or libraries) but i massed up. 

when I try to run f- spot or sysinfo ( or any application) it tells me
```

** (/usr/lib/f-spot/f-spot.exe:9635): WARNING **: The following assembly referenced from /usr/lib/f-spot/f-spot.exe could not be loaded:
     Assembly:   glib-sharp    (assemblyref_index=4)
     Version:    2.12.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/f-spot/).


** (/usr/lib/f-spot/f-spot.exe:9635): WARNING **: Could not load file or assembly 'glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
File name: 'glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f'


```when i want to get mono version it says

```

Mono JIT compiler version 2.4 (tarball Pr&#351; Mar  4 11:19:46 EET 2010)
Copyright (C) 2002-2008 Novell, Inc and Contributors. www.mono-project.com
    TLS:           __thread
    GC:            Included Boehm (with typed GC)
    SIGSEGV:       altstack
    Notifications: epoll
    Architecture:  x86
    Disabled:      none


```What can i do for this error.

---

