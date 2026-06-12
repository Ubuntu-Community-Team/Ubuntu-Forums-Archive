---
title: "Can't Install aDesklets"
date: 2008-01-24
forum: Desktop Effects &amp; Customization
---

### Post by Mark76 on 2008-01-24
I tried to follow instructions elsewhere and this is the result

> mark@Panopticon:~$ cd ~/.desklets/Calendar-0.5.3/ 
[email]mark@Panopticon:~/.desk[/email]lets/Calendar-0.5.3$ ./Calendar.py --xfce4
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./Calendar.py", line 14, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets interpreter initialization error - Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0x97d638>> ignored
Terminated



What should I do about it?

---

### Post by Mark76 on 2008-01-25
Bump

---

