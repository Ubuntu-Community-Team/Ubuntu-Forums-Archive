---
title: "[SOLVED] I broke Compiz - how do I reinstall it?"
date: 2008-02-05
forum: Desktop Effects &amp; Customization
---

### Post by tom66 on 2008-02-05
I managed to break my Compiz install. I've tried to repair it and I've decided that it would probably be best to reinstall it entirely. Can someone give me a script, or instructions to reinstall Compiz, that is, completely remove it and install it again. 

Thanks!

PS: I'm a Linux newbie, so please give me clear instructions. Thanks.

---

### Post by Don Gatto on 2008-02-06
Hello,

In (System -> Administration -> ) Synaptic you should make a search for packages having "compiz" in their names. If you right-click on them you should be able to select 'Mark for Reinstallation'. If this won't work, you'll have to select 'Mark for Complete Removal'. This will remove the selected packages, and their settings too. Then you select those packages again (now marked with white squares) and select 'Mark for Installation'.

Be cautious! :) (These steps shouldn't make unrecoverable problems even in the worst case, though.)

---

### Post by tom66 on 2008-02-06
Hmm, it didn't work, but thanks for your help!

Compiz still works, but CCSM gives me this error. I've got some simple effects: sliding animations, minimization animations and the default Ubuntu animations...

```

thomas@orpheus:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
thomas@orpheus:~$ 

```

---

### Post by Ub1476 on 2008-02-06
Try this:

```
sudo apt-get install ubuntu-desktop --reinstall
```

---

### Post by tom66 on 2008-02-07
I'm still getting an error in the command line:

```

thomas@orpheus:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
thomas@orpheus:~$ 

```

Nothing happened: reinstalling it just left me with the same effects. The sliding animation is nice... but it just doesn't compare to the cube. Or wobbly windows.

Thanks for your help though!
Tom

---

### Post by Don Gatto on 2008-02-07
You said you broke Compiz. How did you do that? Did you upgrade (some parts of) Compiz or Python?

Nevertheless, I've found a topic ([http://forum.compiz-fusion.org/showthread.php?t=4282](http://forum.compiz-fusion.org/showthread.php?t=4282)) about the problem, it was caused by the repository list.

Follow the last few steps (either edit your /etc/apt/sources.list file, or force the same version of the packages, rather both).

---

### Post by tom66 on 2008-02-07
I'm not sure. I just restarted my computer and it broke...

---

### Post by Spoken on 2008-02-07
search "compiz" in synaptic

---

### Post by tom66 on 2008-02-08
I managed to fix it by downgrading it. Thank you for pointing out that post! 

Thanks,
Tom

---

