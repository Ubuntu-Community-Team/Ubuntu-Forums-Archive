---
title: "I am deeper in mud"
date: 2005-09-15
forum: Desktop Environments
---

### Post by Bluefire on 2005-09-15
So, I was at work doing tech support, and VNC'd to my linux box.  I was attempting to uninstall an application manually, and was removing the folder from /usr/bin when I got a call.

In answering the call, I accidentally hit enter with this in a terminal:

sudo rm -R /usr/bin

Oh well, time for a format/reinstall.  ](*,)

---

### Post by matthew on 2005-09-15
Ouch!!

---

### Post by az on 2005-09-15
[QUOTE=Bluefire]So, I was at work doing tech support, and VNC'd to my linux box.  I was attempting to uninstall an application manually, and was removing the folder from /usr/bin when I got a call.

In answering the call, I accidentally hit enter with this in a terminal:

sudo -R /usr/src

Oh well, time for a format/reinstall.  ](*,)[/QUOTE]


What does the -R switch do?  And anyway, you do notneed anything in /usr/src to run your system?

Is that the command you ran?

---

### Post by Bluefire on 2005-09-15
[QUOTE=azz]What does the -R switch do?  And anyway, you do notneed anything in /usr/src to run your system?

Is that the command you ran?[/QUOTE]

Oops, I typed the post wrong.

It was /usr/bin that I accidentally deleted by running sudo rm -R /usr/bin

---

### Post by matthew on 2005-09-15
/usr/bin?? Stink. Removing the source code from /usr/src would make compiling impossible until you downloaded the contents again, though you should still have a working system, but all your executable binaries? Bummer...

azz: rm -R will remove _everything_ including subdirectories and their contents
EDIT: I believe the R stands for recursive

Even worse would have been "sudo rm -R /"

---

