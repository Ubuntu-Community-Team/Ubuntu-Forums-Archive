---
title: "Detect xfwm events with a bash script... is it possible?"
date: 2013-08-09
forum: Desktop Environments
---

### Post by avernalvigil on 2013-08-09
Hi,

I use Xubuntu, and I'm interested to know if it's possible to detect xfwm events (minimize,maximize,close, etc.) using a bash script daemon, or by other means.

---

### Post by ian-weisser on 2013-08-10
Dbus is a convenient way to (many) monitor system and (many) desktop environment events, and to trigger them, too.

Dbus can be used from the command line, python, c, and many many other languages and/or scripts.
The easiest way to see dbus in action is to try the d-feet Dbus browser, included in the d-feet package.

There are several tools to monitor and use dbus from the command line. A dbus command has several parts (bus, destination, path, interface, message, etc.), so the commands all get a bit long and complicated-looking. One good tutorial is at [http://techbase.kde.org/Development/Tutorials/D-Bus/Introduction](http://techbase.kde.org/Development/Tutorials/D-Bus/Introduction)

---

### Post by avernalvigil on 2013-08-10
Hi ian-weisser,

I read the tutorial [http://techbase.kde.org/Development/Tutorials/D-Bus/Introduction](http://techbase.kde.org/Development/Tutorials/D-Bus/Introduction), and this paragraph caught my attention:

> **Signals**
(...) A signal is emitted by the application which is exporting the interface and is available to any application on the same bus. This allows an application to spontaneously advertise changes in state or other events, to any applications which may be interested in tracking those changes.

So I guess I have to find out what signals xfwm sends (using qdbusviewer, probably) and create a script able to react to them. Thank you for pointing out a promising direction!

---

### Post by ian-weisser on 2013-08-12
I find d-feet easier to use when exploring the paths, interfaces, methods, and signals of dbus.

---

