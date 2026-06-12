---
title: "gDesklets daemon does not load"
date: 2005-08-02
forum: Desktop Environments
---

### Post by Aeneas_117 on 2005-08-02
I just installed gDesklets (34.2) via Synaptic, and when i try to run the app by going to applications->accesories->gDesklets, something pops in the taskbar saying "starting gdesklets" --but it never actually gets loaded.

When I type gDesklets in my terminal, I get the following message...

Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/gdesklets/utils/__init__.py", line 23, in _pretty_excepthook
    deep_trace = True)
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 76, in format
    import vfs
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 119, in _new_imp
    module = _old_imp(name, globs, locls, fromlist)
  File "/usr/lib/gdesklets/utils/vfs.py", line 120, in ?
    exists = exists_urllib2
NameError: name 'exists_urllib2' is not defined

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/gdesklets", line 4, in ?
    from main.DisplayList import DisplayList
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 119, in _new_imp
    module = _old_imp(name, globs, locls, fromlist)
  File "/usr/lib/gdesklets/main/DisplayList.py", line 4, in ?
    from utils import vfs
  File "/usr/lib/gdesklets/utils/ErrorFormatter.py", line 119, in _new_imp
    module = _old_imp(name, globs, locls, fromlist)
  File "/usr/lib/gdesklets/utils/vfs.py", line 120, in ?
    exists = exists_urllib2
NameError: name 'exists_urllib2' is not defined

I think something is wrong with python, but what? Thanks in advance for any help/suggestions.

---

