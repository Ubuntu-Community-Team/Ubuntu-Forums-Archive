---
title: "crashed gdesklets"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by guitodd on 2008-04-15
Accidentally unplugged power to computer at boot.  Gdesklets will no longer load.  Tryed to reinstall the packages but nothing.

I get:

>>Cannot establish connection to daemon:  Timeout!
>>The log file might help you solve the problem.

Log file appears to be blank.

Searched the existing posts but nothing seemed to apply directly to my problem since Gdesklets has worked fine until now.

Any ideas?

Running Gutsy on an Intel dual-core, Intel graphics.

---

### Post by Sam Lars on 2008-04-15
When you uninstalled, did you do a complete uninstall in Synaptic or a --purge with aptitude?
```
sudo aptitude remove --purge gdesklets gdesklets-data
```
If that doesn't work, you could try also removing the .gdesklets folder in your home directory.

---

### Post by guitodd on 2008-04-15
OK.. did both and it worked!  Thanks for the help.  Didn't know the 'purge' thingy.

Thanks again!

---

