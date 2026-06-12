---
title: "m64py emulator will not launch"
date: 2014-07-20
forum: Gaming &amp; Leisure
---

### Post by jkdublin00 on 2014-07-20
Hello everyone. I am trying to run a m64py which is a gui front-end for mupen64plus. When running ./m64py in terminal i get the following: 

M64Py - A frontend for Mupen64Plus version 0.2.1


Frontend: INFO: attached to library 'Mupen64Plus Core' version 2.0.0
Frontend: INFO: includes support for Dynamic Recompiler.
Frontend: INFO: video extension enabled
Traceback (most recent call last):
  File "./m64py", line 83, in <module>
    main()
  File "./m64py", line 68, in main
    window = MainWindow((opts, args))
  File "/home/jason/Desktop/m64py-0.2.1/src/m64py/frontend/mainwindow.py", line 88, in __init__
    self.worker.init()
  File "/home/jason/Desktop/m64py-0.2.1/src/m64py/frontend/worker.py", line 56, in init
    self.plugins_load()
  File "/home/jason/Desktop/m64py-0.2.1/src/m64py/frontend/worker.py", line 143, in plugins_load
    self.core.plugin_load_try(plugin_path)
  File "/home/jason/Desktop/m64py-0.2.1/src/m64py/core/core.py", line 222, in plugin_load_try
    plugin_handle = C.cdll.LoadLibrary(plugin_path)
  File "/usr/lib/python2.7/ctypes/__init__.py", line 443, in LoadLibrary
    return self._dlltype(name)
  File "/usr/lib/python2.7/ctypes/__init__.py", line 365, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: libboost_filesystem.so.1.46.1: cannot open shared object file: No such file or directory

Any help is appreciated

---

### Post by angussheehan on 2014-09-11
Bumping this. Same exact console output here, too.

---

### Post by ihelpyou59 on 2014-09-23
Bumping as well, same issue here.......Also having an issue getting cheat codes to work. Get the following output when trying even list cheat codes for a game.

Here's the output:

UI-Console: attached to core library 'Mupen64Plus Core' version 2.0.0
UI-Console:             Includes support for Dynamic Recompiler.
Core: Goodname: Legend of Zelda, The - Ocarina of Time - Master Quest (E) (GC) [!]
Core: Name: THE LEGEND OF ZELDA 
Core: MD5: 1618403427E4344A57833043DB5CE3C3
Core: CRC: 1d4136f3 af63eea9
Core: Imagetype: .z64 (native)
Core: Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
Core: Version: 144c
Core: Manufacturer: Nintendo
Core: Country: Unknown (0xF50)
UI-Console Warning: cheat code database file 'mupencheat.txt' not found.
UI-Console Warning: no cheat codes found for ROM image 'THE LEGEND OF ZELDA'
Core Status: Rom closed.

---

