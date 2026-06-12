---
title: "[SOLVED] CCSM wont run"
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by murt on 2007-12-01
When i try the ccsm command for compiz fusion i get the error
```
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
```

I have installed it all. Does someone know what to do?

---

### Post by erginemr on 2007-12-01
Hello, Please follow the discussions on these two threads, because it defines exactly the same problem as yours:
[http://ubuntuforums.org/showthread.php?t=577614&page=4](http://ubuntuforums.org/showthread.php?t=577614&page=4)
[http://forum.compiz-fusion.org/showthread.php?p=32526](http://forum.compiz-fusion.org/showthread.php?p=32526)

In the first the recommended solution was:
> Originally Posted by damir_1105  View Post
if you updated to gutsy from feisty probably you use compiz from that repositories. try this:

synaptic package manager -> select compizconfig-settings-manager -> Menu -> Package -> Force Version then use 0.5.2 instead 0.6.99.

while in the second, it was:
> Hi,

Had the same problem. The solution that work worked for me:

1. Remove all compiz fusion packages
2. Remove or just move folder ~/.config/compiz <<- that's the one that causes everything
3. Reinstall compiz
4. tada! You'll have to set all your personal settings again, though!

Maybe (haven't tried that myself) you can even suffice with only removing the ~/.config/compiz folder, without the fuzz of removing and reinstalling compiz.. Let me know.
Reply With Quote

Good luck!

---

### Post by murt on 2007-12-01
Thank you very much, and I'm sorry for asking again, did'nt find the old thread :(

---

### Post by erginemr on 2007-12-01
You are most welcome, Did it work? (If so, can you please mark your thread as solved from the "thread tools" above.)

Take Care & Have Fun with Compiz!

---

### Post by murt on 2007-12-02
Yes, it did work. Many thanks :)

---

