---
title: "Karmic -&gt; Lucid upgrade, alt + f4 problem"
date: 2010-08-27
forum: Desktop Environments
---

### Post by mealstrom on 2010-08-27
Hi, after karmic to lucid upgrade  i ve got problem with "**alt + f4**" key combination. 

This should only close window, but it closes window and switch to** tty4** (text mode) like 
**ctrl + alt + f4**

so i can switch between terminals with c**trl + alt +fX** and **alt+fX**. 

I've looked at_ System - Preferences - Shortcuts _and there everything  is ok. 


What i've to do to fix this ?

---

### Post by misha_bear on 2011-02-06
This issue is about this bug:
[https://bugs.launchpad.net/ubuntu/+bug/520546](https://bugs.launchpad.net/ubuntu/+bug/520546)
So the problem is related to console-cyrillic package.
For me commenting out the lines 
# if ($ENCODING eq "unicode") {
#    &execute ("kbd_mode -u");
# } else {
#    &execute ("kbd_mode -a");
# }
out of /usr/bin/cyr script has solved the issue without removing the package, but I don't know what really caused the bug.

---

