---
title: "BIBUS installation issues"
date: 2007-11-02
forum: Education &amp; Science
---

### Post by natousayni on 2007-11-02
hey  every body ! 
glad to join the forum and thanks for all yours advices, i'll be glad to soon participate.
so...
I'm running with ubuntu 7.10 and i've just installed BIBUS through the Synaptic Package Manager system (System/Administration).
As I've been reading in few posts I run for a first time BIBUS trough the terminal as an admin

[FONT="Verdana"]# sudo bibus[/FONT]

here's what I'm getting as an awnser...

[FONT="Verdana"]Traceback (most recent call last):
  File "/usr/bin/bibus", line 142, in <module>
    Bibus = Bibus()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/bin/bibus", line 127, in OnInit
    dlg.Run()
  File "/usr/share/bibus/FirstStart/FirstStart.py", line 118, in Run
    import uno
  File "/usr/lib/python2.5/site-packages/uno.py", line 37, in <module>
    import pyuno
SystemError: dynamic module not initialized properly[/FONT]

Here I got lost. May you help me ?

thanks

Natousayni

---

### Post by akniss on 2007-11-02
> **natousayni said:**
> hey  every body ! 
As I've been reading in few posts I run for a first time BIBUS trough the terminal as an admin


I'm curious where you read to start bibus as sudo... I couldn't find that tip anywhere on the forum.  Have you tried to run it as a normal user?  Did it produce any errors?

---

### Post by natousayni on 2007-11-02
I've read it on an another forum.
but anyway, it give the same...

---

### Post by Spoker on 2007-11-05
There already are some posts about it on the forum. Check out here:

[http://ubuntuforums.org/showthread.php?t=583956&highlight=bibus](http://ubuntuforums.org/showthread.php?t=583956&highlight=bibus)

That solution worked for me!

---

### Post by natousayni on 2007-11-06
Thanks a lot Spoker, it goes perfectly now.

I've looked a big time for that thing and every howtos i've found were datted before 2006 an dBibus official Website show installation process for Breezy Ubuntu version. Maybe it should be great doing a new how to with your advices.

Big Thanks !

Natousayni

---

