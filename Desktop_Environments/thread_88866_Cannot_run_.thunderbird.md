---
title: "Cannot run ./thunderbird"
date: 2005-11-11
forum: Desktop Environments
---

### Post by geokker on 2005-11-11
I've tried Opera, Evolution, Balsa and Sylpheed and I've decided they're all pants so I'm going back to Thunderbird.

I downloaded 1.0.7 from mozilla.org, extracted it and tried to run ./thunderbird on a fairly default breezy.

I get this:

error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I've tried Synaptic for the library but it turns up nothing.

I think I've had Thunderbird running before, but that might be before I wiped Hoary and installed Breezy.

Any ideas?

---

### Post by mrmcctt on 2005-11-11
I run thunderbird just fine.  The way that I installed it was through Synaptic, though.  You can install it from the repositories via Synaptic or you can ```
sudo apt-get install mozilla-thunderbird
``` at the command line and it should take care of set up and dependencies.

Hope this helps.

---

