---
title: "Can't start synaptic after failed attempt to install google earth"
date: 2009-01-26
forum: General Help
---

### Post by Burnasty on 2009-01-26
I tried installing google earth but it won't load.  I thought I could uninstall it with synaptic but when I tried opening it I get an error message that says
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any help is much appreciated.

---

### Post by mb_webguy on 2009-01-26
As it says, you need to run the command "sudo dpkg --configure -a" in the terminal to correct the problem.  After that, you should be able to open and use Synaptic as usual.

---

### Post by Burnasty on 2009-01-26
That fixed it.  I didn't want to do something and make it worse.  I know just enough to break stuff.

---

