---
title: "why is wish opening two windows?"
date: 2010-11-21
forum: Desktop Environments
---

### Post by fabjoa on 2010-11-21
Hi,

In Tcl/Tk, the source of file /usr/bin/wan27

#! /usr/bin/wish -f
set w .main
toplevel $w
wm title $w "FOO"

when issuing the command "wan27" from terminal (Linux/Debian/Ubuntu 10.04), it opens two windows, one with the title wan27 and the other one with the title FOO. I just want the FOO window to open. How can I fulfill that?

Thanks

[edit]solved there [http://stackoverflow.com/questions/4238246/why-is-wish-opening-two-windows-instead-of-one](http://stackoverflow.com/questions/4238246/why-is-wish-opening-two-windows-instead-of-one) for those having the same problem[/edit]

---

