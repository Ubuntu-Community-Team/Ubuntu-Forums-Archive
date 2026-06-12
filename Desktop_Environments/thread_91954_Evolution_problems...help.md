---
title: "Evolution problems...help"
date: 2005-11-18
forum: Desktop Environments
---

### Post by potrick on 2005-11-18
Hey everyone. I'm really loving Ubuntu thus far.

  Anyway, I can't seem to start up Evolution. When I try, this message comes up:

The Application "evolution" has quit unexpectedly.

Starting it in terminal gives us all this:

(evolution:8694): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:8694): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:8694): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' is invalid for instance `0x81f2978'

(evolution:8694): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' is invalid for instance `0x81f2978'

(evolution:8694): GLib-GObject-WARNING **: gsignal.c:1716: signal `toggled' is invalid for instance `0x81f2978'
potrick@x-potifer:~$



Any ideas, anyone?

---

### Post by cstudent on 2005-11-18
How long have you had Ubuntu installed?

Is this the first instance you have tried Evolution? Was it working?

Did you install any new software or libraries that might have effected Evolution?

I'm no expert, but I read the error as a possibly corrupted install of Evolution or a library file.


Bill

---

### Post by potrick on 2005-11-19
I've had ubuntu installed for about a month. I have been using evolution as a calendar the entire time without any problems. I cannot think of any software I have installed that may effect Evolution.

Is it possible that reinstalling Evolution would fix the problem? Is reinstalling something as integrated into Ubuntu even possible? 

Thank you so much for getting back to me, cstudent. I appreciate it.

---

### Post by cstudent on 2005-11-19
You can go into Synaptic and search for Evolution. There's an option to mark for reinstallation. It can't hurt to try that.

---

### Post by potrick on 2005-11-19
reinstalled everything related to evolution. Nothing. And for the record I tried deleting my settings (home/.evolution) earlier with no positive effects.

---

### Post by cstudent on 2005-11-19
I wish I had a solution for you. My next step, since nobody on the forum seems to have an answer, would be be to try the Evolution page directly.

[http://www.gnome.org/projects/evolution/](http://www.gnome.org/projects/evolution/)

They have an irc channel listed. You might find someone on there who would know what's going on if they saw your error message. They also have a mailing list you could search. Maybe it's come up there before.

Wish I could be a better service. Good luck.

Bill

---

### Post by jlx on 2005-11-19
I had the same problem: I can't start ubuntu. The solution that works for me was to change the theme. I think I had Alphacube and now I had Industrial (beautiful with Gentleman Metacity theme). That worked for me. I had problems in Calendar section; if you have problems in a specific section try this command: evolution --component=mail otherwise starts in last section you close Evolution.
Good luck.

---

### Post by Orval on 2005-11-29
Take a look at [this]("http://ubuntuforums.org/showthread.php?p=529446#post529446") thread. Maybe it helps you.

---

