---
title: "What does this warning mean?"
date: 2005-11-18
forum: Desktop Environments
---

### Post by spencer on 2005-11-18
Hi, I just installed thunderbird and this warning was given. What does it mean?
```
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 56661 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.0.7-0ubuntu05.10_i386.deb) ...
Successful preinst
Setting up mozilla-thunderbird (1.0.7-0ubuntu05.10) ...
Updating mozilla-thunderbird chrome registry...find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

done.
```

I have no problems with Thunderbird, runs great! 

-spencer

---

### Post by Kyral on 2005-11-18
I have no clue, but if its working fine then don't worry about it :D

---

### Post by cstudent on 2005-11-18
Looks like it is saying the option -maxdepth is placed in the wrong place. It's not something you have done, but looks like an error in apt somewhere. The way I read the error code, it looks like things will just be ignored.

Bill

---

### Post by spencer on 2005-11-18
I just had just finished a clean install of Breezy and installed Thunderbird, so the system was fresh. I won't worry much about it, Thanks for the responses. 

-spencer

---

