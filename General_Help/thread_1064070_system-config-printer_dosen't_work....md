---
title: "system-config-printer dosen't work..."
date: 2009-02-08
forum: General Help
---

### Post by Racecar56 on 2009-02-08
When I try to configure the printer, it doesn't work...
Verbose output:
```
system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 30, in <module>
    import dbus
ImportError: No module named dbus
```
I even tried doing this:
```
sudo apt-get install libdbus*
```
That didn't work so I tried this:
```
sudo apt-get install python-libdbus*
```
One again, didn't work.
Tried this:
```
sudo apt-get install libdbus*-python*
```
Didn't get anything.
What do I do? I'm running a old HP Pavilion dv5000 with Ubuntu 8.10.
All updates are installed.
(By the way, this isn't my laptop, its my friend's.)
[COLOR="Sienna"]W[/COLOR][COLOR="Red"]O[/COLOR][COLOR="Yellow"]O[/COLOR][COLOR="Lime"]T[/COLOR] [COLOR="Indigo"]5[/COLOR][COLOR="Magenta"]0[/COLOR][COLOR="Purple"]T[/COLOR][COLOR="Black"]H[/COLOR] [COLOR="Red"]P[/COLOR][COLOR="Magenta"]O[/COLOR][COLOR="Navy"]S[/COLOR][COLOR="DarkOrange"]T[/COLOR][COLOR="Red"]![/COLOR][COLOR="Black"]![/COLOR][COLOR="DarkGreen"]![/COLOR][COLOR="SandyBrown"]![/COLOR][COLOR="Magenta"]![/COLOR][COLOR="Cyan"]1[/COLOR]
EDIT: Fixed some typos, made the 50th post celebration colorful, and given a reason to edit.

---

### Post by utnubuuser on 2009-02-08
dbus in synaptic yields this> D-Bus is a message bus, used for sending messages between applications.
Conceptually, it fits somewhere in between raw sockets and CORBA in
terms of complexity.

D-Bus supports broadcast messages, asynchronous messages (thus
decreasing latency), authentication, and more. It is designed to be
low-overhead; messages are sent using a binary protocol, not using
XML. D-Bus also supports a method call mapping for its messages, but
it is not required; this makes using the system quite simple.

It comes with several bindings, including GLib, Python, Qt and Java.

This package contains the D-Bus daemon and related utilities.

The client-side library can be found in the libdbus-1-3 package, as it is no
longer contained in this package.

and dbus seems to be installed on a default installation.
Maybe libdbus-1-3?

Maybe try doing a reconfigure with > sudo dpkg --configure -a

---

### Post by Racecar56 on 2009-02-09
Sadly, that did no good. :(

---

### Post by ngvrnd on 2009-11-09
I had this problem, and it turned out that I had changed the system bin path in /etc/bash.bashrc and /etc/profiles/ to point to a variant python executable which didn't have the import path for dbus.  When  I fixed this, the system-config-printer script worked fine again.  You may have a similar problem.

---

