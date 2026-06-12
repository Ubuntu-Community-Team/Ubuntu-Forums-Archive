---
title: "ccsm (compiz settings maneger) does not load"
date: 2010-05-06
forum: Desktop Environments
---

### Post by guruyaya on 2010-05-06
Hi all
I have a problem starting the effects manager of compiz, on Ubuntu 10.4 64 bit , that I just upgraded from 9.10. 
It just won't start from the gnome menu. Trying to start it up from command line gives a line that goes "Loading Icons..." and just gets stuck there. xorg logs did not show any response while starting it up. 

Any idea why?

---

### Post by guruyaya on 2010-05-06
I've found that it gets stuck in the python function gtk.main() if it helps anyone.
Anyone?

---

### Post by kid1000002000 on 2010-05-09
have you tried to do a COMPLETE REMOVAL and re installation from synaptic?

---

### Post by guruyaya on 2010-05-09
I'm not sure what complete removal means, but I've uninstalled, then re-installed the package named "compiz-settings-maneger"/ :guitar:

---

### Post by kid1000002000 on 2010-05-09
you might want to try reinstalling "compiz" itself too.  If that doesn't work, unless somebody doesn't know the specific thing that is wrong on your system, just try reinstalling anything that shows up when you search for "compiz" in synaptic manager.

If you right click on compiz in synaptic and click on "complete removal," rather than just uninstall, that could do the trick too.  I'm not sure which package is having difficulty though, so you'll have to guess or just hit all of them.

---

### Post by locodog on 2010-11-21
I'm having same problem, I click CompizConfig Settings Manager, and window doesn't open...
When I typed ccsm in console, i've got this output, maybe somebody will understand and help me solve problem.
(I've tried complete removal of anything related to compiz and reinstalling, but same thing happens).
```
process:2507): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 100, in <module>
    import ccm
  File "/usr/lib/python2.6/dist-packages/ccm/__init__.py", line 1, in <module>
    from ccm.Conflicts import *
  File "/usr/lib/python2.6/dist-packages/ccm/Conflicts.py", line 27, in <module>
    from ccm.Constants import *
  File "/usr/lib/python2.6/dist-packages/ccm/Constants.py", line 88, in <module>
    locale.setlocale(locale.LC_ALL, "")
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

---

