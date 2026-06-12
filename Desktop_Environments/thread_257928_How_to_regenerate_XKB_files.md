---
title: "How to regenerate XKB files?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by krugger on 2006-09-15
I have a slightly modified ubuntu install - :)

And when I updated my Xorg, my xkb files in /usr/X11R6/lib/X11/xkb became 0 byte sized.

drwxr-xr-x  2 root root 4096 2006-09-15 12:06 compat
-rw-r--r--  1 root root    0 2006-05-18 10:47 compat.dir
lrwxrwxrwx  1 root root   12 2006-09-15 12:09 compiled -> /var/lib/xkb
drwxr-xr-x  5 root root 4096 2006-09-15 12:06 geometry
-rw-r--r--  1 root root    0 2006-05-18 10:47 geometry.dir
drwxr-xr-x  4 root root 4096 2006-09-15 12:06 keycodes
-rw-r--r--  1 root root    0 2006-05-18 10:47 keycodes.dir
drwxr-xr-x  5 root root 4096 2006-09-15 12:06 keymap
-rw-r--r--  1 root root    0 2006-05-18 10:47 keymap.dir
drwxr-xr-x  2 root root 4096 2006-09-15 12:06 rules
drwxr-xr-x  2 root root 4096 2006-09-15 12:06 semantics
-rw-r--r--  1 root root    0 2006-05-18 10:47 semantics.dir
drwxr-xr-x 11 root root 4096 2006-09-15 12:06 symbols
-rw-r--r--  1 root root    0 2006-05-18 10:47 symbols.dir
drwxr-xr-x  2 root root 4096 2006-09-15 12:06 types
-rw-r--r--  1 root root    0 2006-05-18 10:47 types.dir
lrwxrwxrwx  1 root root   16 2006-09-15 12:09 xkbcomp -> /usr/bin/xkbcomp

And the compiled directory is empty. This causes Xorg not to be able to load the right keymap and falling back to default keymap. Can anyone tell me how to regenerate the .dir files? Or should I just copy it from another Ubuntu install?

---

### Post by krugger on 2006-09-16
I figured out that I can use xkbcomp to read and compile, but I don't get the expected output. File reports a compiled xkm file, and I don't get the old lists.

Anyone know how to get keyboard layouts without xkb?

---

