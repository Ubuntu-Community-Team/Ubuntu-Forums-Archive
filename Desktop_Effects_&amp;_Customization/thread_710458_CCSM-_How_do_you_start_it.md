---
title: "CCSM- How do you start it?"
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by sircx on 2008-02-28
I'm new to Linux and Ubuntu, and slowly learning how to do everything in the terminal. I see all these great desktop effects and learned it has something to do with something called the ccsm. Please tell me all you know about it and how to start it through the terminal. I tried someone's code and got this error:
[I]
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'[/I]

This was the code I entered:

*~$ ccsm*

---

### Post by Therion on 2008-02-28
First you'll need to install it, and before you can install you need to enable the Repositories for it.  Navigate to:  System > Administration > Software Sources
And put check marks in the two remaining repository boxes.  Update your lists when prompted.

Now install CCSM by using Synaptic.  Search on **compizconfig-settings-manager** and install it.

Once it's installed, go here and learn how to start doing some cool Compiz' related stuff:  [How to Set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).  You've already got everything installed at this point so you can skip all that.

---

