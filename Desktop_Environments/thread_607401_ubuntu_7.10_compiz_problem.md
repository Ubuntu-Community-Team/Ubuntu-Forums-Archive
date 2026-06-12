---
title: "ubuntu 7.10 compiz problem"
date: 2007-11-08
forum: Desktop Environments
---

### Post by slowz3r on 2007-11-08
When i go to System>preferences and then Compiz settings manager i cant get that to open up.  Another problem is i have the visual effects settings set to Extra, but i see no effects.  Any ideas?

---

### Post by Perpetual on 2007-11-08
launch ```
ccsm
``` from a terminal to see any errors and post the results here.

---

### Post by maximuss77 on 2007-12-17
i have the same problem here is what mine says: 


derek@maximuss-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
derek@maximuss-desktop:~$ 



Ps im completely new to linux..

---

### Post by Perpetual on 2007-12-18
> **maximuss77 said:**
> i have the same problem here is what mine says: 


derek@maximuss-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
derek@maximuss-desktop:~$ 



Ps im completely new to linux..

Where did you install ccsm from?  Was it a third party repo?  Did you install ccsm from the ubuntu repositories?

could try...

```
sudo apt-get remove --purge compizconfig-settings-manager
```

after that:

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by giannis1_86 on 2007-12-18
thanks....i had the same problem....

---

### Post by Perpetual on 2007-12-18
> **giannis1_86 said:**
> thanks....i had the same problem....

Out of curiosity, did that fix the problem...removing and installing again?

---

### Post by giannis1_86 on 2007-12-18
for me yes.....


it worked....

---

### Post by Perpetual on 2007-12-18
> **giannis1_86 said:**
> for me yes.....


it worked....

Ok, thanks!

---

