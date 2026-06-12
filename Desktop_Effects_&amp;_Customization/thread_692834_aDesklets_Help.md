---
title: "aDesklets Help"
date: 2008-02-10
forum: Desktop Effects &amp; Customization
---

### Post by nami on 2008-02-10
Hi

I was impressed with the following desklet:

[http://gnome-look.org/content/show.php/CircleMeter+adesklet?content=69600](http://gnome-look.org/content/show.php/CircleMeter+adesklet?content=69600)

So I tried installing it and I keep getting the following

> nami@nami-laptop:~/.desklets/CircleMeter$ python mem_meter.py --nautilus
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "mem_meter.py", line 1, in <module>
    from circlemeter import *
  File "/home/nami/.desklets/CircleMeter/circlemeter.py", line 6, in <module>
    from statgrab import *
ImportError: No module named statgrab
[email]nami@nami-laptop:~/.desk[/email]lets/CircleMeter$ 

And the circular desklet does not show up on my desktop.  What am I doing wrong?  This is the first time I have tried using aDesklets...

---

### Post by Rupertronco on 2008-02-10
The error says "No module named statgrab." The installation instructions indicate that you need the python-statgrab package. I'm not in ubuntu right now so I can't check the repos to see what the exact package name is. 

Try ```
apt-cache search statgrab
```

see if that python package appears, install it, and try to run the circle meter again. If it brings up another error, post it here.

---

