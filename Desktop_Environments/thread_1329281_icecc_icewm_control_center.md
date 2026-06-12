---
title: "icecc icewm control center"
date: 2009-11-17
forum: Desktop Environments
---

### Post by M4rotku on 2009-11-17
Hey Guys,

I really like icewm, but there are some difficulties which I cannot get over and thus am still using gnome for a lot of tasks.  I think I could get everything working properly if I could get the icewm control center working.  I know of other systems that has it installable by default, but for some reason we don´t.  I tried to install via [this]("http://www.icewm.org/FAQ/IceWM-FAQ-11.html#ss11.5"), but it didn´t work.  When I tried to run it after installing it, I received the following error:

> icecc: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Any help is much appreciated.

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-11-17
I found the iceme package which is one of several which I wanted, but it is only for dapper.

Here is where I found it:

[http://packages.ubuntu.com/dapper/amd64/x11/iceme]("http://packages.ubuntu.com/dapper/amd64/x11/iceme")

Would this still work?  or would it break something?

---

### Post by M4rotku on 2009-11-20
I tried converting an .rpm package for the iceme version from a few years back (iceme-1.0.0-1.noarch.rpm) and received an error when converting (with alien).  When I tried to install the package anyways, it installed, but came up with a bunch of errors when I tried to run it.

I haven't found any other solutions yet.  Any advice would be much appreciated.  If other icewm users are reading this, how do you configure your system?  Do you all just use the text files?  If so, if you could leave me some tips as to how to configure my menu files, it would be greatly appreciated.  Currently, when I try to edit them, it just leads me on a chase down the rabbit hole looking for different menu files from which it derives.

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-11-26
bump

---

### Post by M4rotku on 2009-12-07
Ok, i found out that the menu editor package is out-of-date.  Can anyone give me a method of making my icewm menu update automatically with new programs like the Gnome menu does?  Also, it would be nice if I could get the same categories.  I really feel that I prefer icewm over fluxbox, but this is something that it seems to severely lack.

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-12-09
bump

---

### Post by Ibidem on 2009-12-29
I had that problem back when I used Dapper; I installed  "menu" via Synaptic, which solved it.
Dapper was great with IceWM; some packages are not available for anything else.
If you want try getting icecc to work, you might try installing libstdc++5...
It has the right library.
I've used IceWM since '07 (on Dapper), and I like it too.

To update the menus, run "menu-update" (IIRC).  When installing a package, it will automatically run.

---

### Post by Ibidem on 2010-01-08
Hello again,
icecc definitely does use libstdc++5.  I have installed both, and-
IT WORKS!
Ibidem

---

