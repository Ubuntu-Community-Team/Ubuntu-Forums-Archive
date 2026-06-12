---
title: "How to install xbox 360 controller drivers"
date: 2009-06-17
forum: Gaming &amp; Leisure
---

### Post by keypox on 2009-06-17
I tried to follow this guide but got errors after making the file [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

---

### Post by keypox on 2009-06-17
so i found this site with updated drivers, but dont know how to install them. 

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

I tried another guide which also is outdated and didint work. [http://ubuntuforums.org/showthread.php?t=825464](http://ubuntuforums.org/showthread.php?t=825464)

Follwing the read me i get this error after running scons

keypo@keypo-desktopU:~/Desktop/xboxdrv-linux-0.4.6$ scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/command_line_options.o -c -g -O2 -Wall -ansi -pedantic src/command_line_options.cpp
g++ -o src/evdev_helper.o -c -g -O2 -Wall -ansi -pedantic src/evdev_helper.cpp
src/evdev_helper.cpp:19:22: error: X11/Xlib.h: No such file or directory
src/evdev_helper.cpp:590: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:590: error: template argument 1 is invalid
src/evdev_helper.cpp:590: error: template argument 3 is invalid
src/evdev_helper.cpp:590: error: template argument 4 is invalid
src/evdev_helper.cpp:608: error: 'Display' has not been declared
src/evdev_helper.cpp: In constructor 'Keysym2Keycode::Keysym2Keycode()':
src/evdev_helper.cpp:596: error: 'Display' was not declared in this scope
src/evdev_helper.cpp:596: error: 'dpy' was not declared in this scope
src/evdev_helper.cpp:596: error: 'XOpenDisplay' was not declared in this scope
src/evdev_helper.cpp:604: error: 'XCloseDisplay' was not declared in this scope
src/evdev_helper.cpp: In member function 'void Keysym2Keycode::process_keymap(int*)':
src/evdev_helper.cpp:611: error: 'XDisplayKeycodes' was not declared in this scope
src/evdev_helper.cpp:615: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:615: error: 'keymap' was not declared in this scope
src/evdev_helper.cpp:617: error: 'XGetKeyboardMapping' was not declared in this scope
src/evdev_helper.cpp:621: error: 'NoSymbol' was not declared in this scope
src/evdev_helper.cpp:623: error: expected `;' before 'keysym'
src/evdev_helper.cpp:628: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:632: error: 'XFree' was not declared in this scope
src/evdev_helper.cpp: In function 'int xkeysym2keycode(const std::string&)':
src/evdev_helper.cpp:640: error: 'KeySym' was not declared in this scope
src/evdev_helper.cpp:640: error: expected `;' before 'keysym'
src/evdev_helper.cpp:642: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:642: error: 'NoSymbol' was not declared in this scope
src/evdev_helper.cpp:647: error: 'KeySym' cannot appear in a constant-expression
src/evdev_helper.cpp:647: error: template argument 1 is invalid
src/evdev_helper.cpp:647: error: template argument 3 is invalid
src/evdev_helper.cpp:647: error: template argument 4 is invalid
src/evdev_helper.cpp:647: error: expected initializer before 'i'
src/evdev_helper.cpp:648: error: 'i' was not declared in this scope
src/evdev_helper.cpp:648: error: request for member 'end' in 'sym2code.Keysym2Keycode::mapping', which is of non-class type 'int'
src/evdev_helper.cpp:655: error: 'keysym' was not declared in this scope
src/evdev_helper.cpp:655: error: 'XKeysymToString' was not declared in this scope
scons: *** [src/evdev_helper.o] Error 1
scons: building terminated because of errors.

---

### Post by keypox on 2009-06-17
sweet got it to owrk just gotta follow the readme in the newest driver. 

Help here [http://ubuntuforums.org/showthread.php?t=825464&page=15](http://ubuntuforums.org/showthread.php?t=825464&page=15)

---

### Post by keypox on 2009-06-18
Disregard... thanks for the driver.

Thanks

---

