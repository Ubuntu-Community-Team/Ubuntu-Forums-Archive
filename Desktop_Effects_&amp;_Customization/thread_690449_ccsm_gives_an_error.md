---
title: "ccsm gives an error"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by Atrus6 on 2008-02-07
Whenever I run ccsm I get this error:

atrus@atrus:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
atrus@atrus:~$ 

how do I fix that?

EDIT:  I'm using gutsy, and I get some basic effects (CRTL+Mouse Wheel give transparency, mouse wheel on desktop switches) but, I can't manage anything at all.

---

### Post by Spoken on 2008-02-07
reinstall compiz through synaptic, that might clear any hitches in your setup.

---

### Post by Atrus6 on 2008-02-07
I looked up compiz on the synaptic and reinstalled everything (right click reinstall) , everything that I had installed.  I restarted, and tried ccsm again.  Same exact error.

---

### Post by Atrus6 on 2008-02-07
Ah, got it.

Conflict between versions.
All fixed now.

---

