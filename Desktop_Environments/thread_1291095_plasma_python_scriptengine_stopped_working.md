---
title: "plasma python scriptengine stopped working"
date: 2009-10-14
forum: Desktop Environments
---

### Post by nerdy_kid on 2009-10-14
the python script engine just suddenly stopped working.  when i run plasmoid viewer from commandline:

```

findServiceByDesktopPath:  not found
Traceback (most recent call last):
  File "/usr/share/kde4/apps/plasma_scriptengine_python/pyappletscript.py", line 21, in <module>
    from PyKDE4.plasma import Plasma
ImportError: No module named plasma
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 100, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL), 'w')
OSError: [Errno 13] Permission denied: '/var/crash/_usr_bin_plasmoidviewer.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/share/kde4/apps/plasma_scriptengine_python/pyappletscript.py", line 21, in <module>
    from PyKDE4.plasma import Plasma
ImportError: No module named plasma

```


please help, this really sucks as i use(d) this engine a lot...

---

### Post by charles.figura on 2009-10-14
It's not just the plasmoidviewer tool.  Looks like it happened with last night's/yesterdays new version of the python/kde/plasma packages on Karmic.  Mine were fine until I rebooted this morning.

---

### Post by nerdy_kid on 2009-10-14
hmm, any idea of what package(s) in particular?  Cause the package cache still has the old version(s)...

---

### Post by charles.figura on 2009-10-14
> **nerdy_kid said:**
> hmm, any idea of what package(s) in particular?  Cause the package cache still has the old version(s)...

Yep... according to the installation history on synaptic:
python-kde4 (4:4.3.2-0ubuntu1) to 4:4.3.2-0ubuntu2
python-kde4-dev (4:4.3.2-0ubuntu1) to 4:4.3.2-0ubuntu2

I'm going to try reverting and see if that clears things up.

---

### Post by nerdy_kid on 2009-10-14
kpackagekit doesn't have the nice feature of history logging (yet?) so i couldn't find them...thanks :)

---

### Post by charles.figura on 2009-10-14
> **nerdy_kid said:**
> kpackagekit doesn't have the nice feature of history logging (yet?) so i couldn't find them...thanks :)

Yeah, neither did adept (as I recall) - that's why I've been using synaptic for years now.  I prefer KDE to gnome, but they still haven't figured out some obvious (to me, anyway) things that gnome has.

---

### Post by nerdy_kid on 2009-10-14
yeah, i seem to be using gnome and kde equally....i tried downgrading, didn't work, i'll have to wait till the next update. that sucks...back to gnome in the meanwhile

---

