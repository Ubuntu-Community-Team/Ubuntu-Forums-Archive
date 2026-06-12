---
title: "Pioneers"
date: 2008-11-19
forum: Gaming &amp; Leisure
---

### Post by RogerTX on 2008-11-19
I've been running Ubuntu about a year, and really enjoying it.  Recently, I'm trying to play Pioneers (a Settlers of Catan) over the LAN with a Windows machine.

The Windows client is running version 0.12, but the downloadable Linux version via Ubuntu is running 0.11, so Windows cannot connect.  Temporarily, I downgraded the Windows client to 0.11, but that version is pretty buggy on Windows.

I then tried to download the 0.12 source and build it on Ubuntu, only to be told that I lacked GLIB2 and Gtk+; I think I actually have them; when I try to install them using "sudo apt-get install glib2", I'm told that the package does not exist.  I'm have some games that use Gtk+, so I'm pretty sure I have that also.

My first attempt to "fix" this by creating symbolic links in /usr/lib/pkgconfig got me through the 'configure' script, but the compiles blow up.

So, I'm stuck.

Help?

---

### Post by olejorgen on 2008-11-19
You probably need to install the development packages for glib and gtk+.
```

sudo apt-get build-dep pioneers
```
will probably install everything you need.

---

### Post by DieB on 2008-11-19
it is:

libglib2.0-dev

and

libgtk2.0-dev

hope that works (,too)

---

### Post by bonkey on 2010-01-05
oops wrong post <<delete this>>

---

