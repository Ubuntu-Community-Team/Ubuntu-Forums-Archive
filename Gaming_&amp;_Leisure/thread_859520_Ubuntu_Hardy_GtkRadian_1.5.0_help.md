---
title: "Ubuntu Hardy GtkRadian 1.5.0 help"
date: 2008-07-14
forum: Gaming &amp; Leisure
---

### Post by Somtin on 2008-07-14
Since my update to Ubuntu Hardy Heron, my GtkRadiant has stopped working. GtkRadiant hangs for about 20 seconds, then spits out this error message:

```
radiant/main.cpp:186
runtime error: GTK+ error: Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
```

Any ideas?

Apologies if this is posted in the wrong forum.

---

### Post by Vadi on 2008-07-14
Try finding an up-to-date binary of GtkRadiant? Your GTK enviroment was also upgraded, and it might be that whatever GtkRadiant was doing isn't valid anymore.

---

### Post by Somtin on 2008-07-14
I downloaded the .rpm and used alien on it to get a .deb

the problem is, is that the latest build is in 2006.. slightly unhelpful.

I'll try compiling the source, and see if that works.


Is it possible to downgrade my GTK environment ?

EDIT:
ew, compiling produces lots of warnings..
Also, it seems that there is a new GtkRadiant 1.6.0 aka ZeroRadiant. Perhaps I should try that..

EDIT 2:
compile did not work, trying ZeroRadiant

---

### Post by Somtin on 2008-07-24
Sorry about the bump, but I am still having trouble and looking for some more specific answers..

How would I go about downgrading GTK+ ? 

I have tried compiling both gtkradiant and ZeroRadiant, both give a segfault!

Thanks in advance for all help!

Somtin

---

### Post by Vadi on 2008-07-24
Are you on 32bit or 64bit? I compiled GtkRadiant (couldn't find ZeroRadiant sources) and it seems to start OK - except the programs loops on me since I don't have the project files (which is pretty bad logic. Do you have the project files? No. Error! Please give them to me. Do you have the project files? No. Error! Please give them to me... ad infinitum).

---

### Post by Somtin on 2008-07-25
32bit.

Can you create a tar.bz2 or tar.gz or something, and upload it somewhere?

What place did you download that source from?

---

### Post by Vadi on 2008-07-25
Oh I'm on 64bit.

I followed these instructions:

[https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/COMPILING](https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/COMPILING)

Except "run 'python ./GtkRadiant/install.py'" didn't work - but what I did was run radiant.bin directly.

---

### Post by Allochtoon on 2008-11-18
> **Vadi said:**
> Oh I'm on 64bit.

I followed these instructions:

[https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/COMPILING](https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/COMPILING)

Except "run 'python ./GtkRadiant/install.py'" didn't work - but what I did was run radiant.bin directly.

having same issue

```
marco@lenovo:~/GtkRadiant/GtkRadiant/install$ ./radiant.bin
I/O warning : failed to load external entity "/home/marco/GtkRadiant/GtkRadiant/install/global.xlink"
I/O warning : failed to load external entity "/home/marco/GtkRadiant/GtkRadiant/install/installs/UrTPack/game/game.xlink"
Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

Segmentation fault

```
when i click edit _> preferences _> global

---

### Post by Somtin on 2008-11-18
Er, actually its been working for me for awhile now. :-P

Should I tar up my radiant and send it to you, Allochtoon?

---

### Post by Allochtoon on 2008-11-19
> **Somtin said:**
> Er, actually its been working for me for awhile now. :-P

Should I tar up my radiant and send it to you, Allochtoon?

I made a new thread:

[http://ubuntuforums.org/showthread.php?t=987100](http://ubuntuforums.org/showthread.php?t=987100)

It might be helpful :)

---

