---
title: "CompizConfig Manager doesn't run"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by Vlux on 2007-10-26
I just installed Ubuntu 7.10 (sorry, a newbie still) and I'm trying to get Compiz Fusion to work. I installed the compiz config settings manager via Synaptic Package manager and it shows up under my Prefernces tab. However, when I click on it, it won't launch and nothing seems to happen. I lurked around here and saw a post saying that I need to restart my X-server or something by pressing ctrl+alt+backspace when I log out, but it's still the same. Am I missing something or just doing something wrong? Thanks in advance.

---

### Post by caffienefree on 2007-10-26
If you type **ccsm** into the terminal, what is the output?

---

### Post by Vlux on 2007-10-26
```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: /var/lib/python-support/python2.5/compizconfig.so: undefined symbol
: ccsStringToEdges

```

That's the output.

---

### Post by rancid98 on 2007-10-26
I seem to be having the same problem.  I removed Trevino's repository as per the sticky in this forum.  I have the visual effects tab in appearance preferences, with the preferences button, but selecting this does nothing, as does selecting the CompizConfig Settings Manager in System Preferences.  Typing CCSM in the Terminal Window gives a slightly different output to the original poster:

```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

Thanks

---

### Post by KRiODOXiS on 2007-10-27
i have the same problem... :S

this is my terminal output

```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

any suggestions?

---

### Post by rancid98 on 2007-10-27
I figured there was something wrong with the installation, so I went to Applications-Add/Remove, searched for Compiz and removed the CompizConfig Manager.  I then reinstalled it and it started working.  Hope this works for you guys.:)

---

### Post by ishaq on 2007-10-31
It worked for me too! Thanks!

---

### Post by Metaphysical on 2007-10-31
> **rancid98 said:**
> I figured there was something wrong with the installation, so I went to Applications-Add/Remove, searched for Compiz and removed the CompizConfig Manager.  I then reinstalled it and it started working.  Hope this works for you guys.:)

yeah, i had the same problem and this also fixed it.:guitar:

---

