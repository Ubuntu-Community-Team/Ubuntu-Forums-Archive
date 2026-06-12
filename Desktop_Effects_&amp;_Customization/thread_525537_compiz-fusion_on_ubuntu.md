---
title: "compiz-fusion on ubuntu"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by bricksen on 2007-08-14
I tried to start it after install but got this message:

Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.

I use nvidia geforce 6600 isn't it compatible with the needed 3d stuff?

---

### Post by hyperair on 2007-08-14
It is. Please insert this at the bottom of your /etc/X11/xorg.conf file:
```

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

---

### Post by DGentry on 2007-10-27
How do you insert this? I keep getting a message saying I cant save it.

---

### Post by Silent Warrior on 2007-10-27
Open it via a terminal, and type 'sudo' first. Then you get to save. :)

(That is: Start your terminal. Then type 'sudo [editor of choice] /etc/X11/xorg.conf' and rejoice.)

---

### Post by DGentry on 2007-10-28
Thanks, I was making a typo but I got it in there now. Hmmm still doesn't work though. I do notice when I go to system / prefs / and try to launch Compiz Config manager it won't launch. The little icon looks like a little blue folder thing with a wrench instead of a real icon if that makes any sense.

I'm kind of thinking something didn't load or install correctly.

---

### Post by hyperair on 2007-10-28
CompizConfig Settings Manager is supposed to look like that actually. Could you try (in a terminal) using the command "ccsm" and see the output?

---

### Post by DGentry on 2007-10-28
Here ya go.

doug@doug-linux:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
doug@doug-linux:~$

---

### Post by hyperair on 2007-10-28
Strange. Did you compile Compiz Fusion from source or install it from a repository? If repository, which repository did you get it from?
```
dpkg --list | grep compiz
```

---

