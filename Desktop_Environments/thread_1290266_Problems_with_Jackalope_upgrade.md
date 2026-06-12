---
title: "Problems with Jackalope upgrade"
date: 2009-10-13
forum: Desktop Environments
---

### Post by psmc on 2009-10-13
I upgraded from Hardy Heron to Jaunty Jackalope. I went to reinstall some apps and i started getting error messages.  Certain libraries were no longer present, SVGA could not be found and then I saw that certain apps i had on 8.04 were not installed on hardy Heron because apparently the vendor no longer supported my machine.  Epiphany web browser was one example.

Now the apps I installed before are the exact same one I am trying to install now.  These apps worked before.  Whats going on?  Does Jackalope not have certain libraries? Why would apps no longer be able to be installed? Also I can' t beelive my machine is suddenly obsolete and no longer supported.

Should I scrap Jackalope and re-install Hardy Heron ?

---

### Post by oldfred on 2009-10-13
I am running Jaunty and I go out to synaptic and I see  Epiphany. Was there some problem in your upgrade?

I would run from the terminal.

# updates
```
sudo apt-get update && sudo apt-get upgrade
```

---

