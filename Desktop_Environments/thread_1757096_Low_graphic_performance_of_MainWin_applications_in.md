---
title: "Low graphic performance of MainWin applications in 11.04"
date: 2011-05-13
forum: Desktop Environments
---

### Post by cioma on 2011-05-13
I use Mentor HyperLynx under Natty 11.04 x64. This is a MainWin application and both under Unity and Classic desktop it takes very long to re-draw graphics (menus etc.)
Same applies to Mentor DxDesigner - it takes very long to start it up and then to react on user input.

Does anyone have similar problems with this or other MainWin application?

---

### Post by cioma on 2011-07-03
bump

---

### Post by wildmanne39 on 2011-07-03
> **cioma said:**
> bumpHi, you might have a look at this link it usually fixes choppy or lagging graphics.

[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

---

### Post by cioma on 2011-07-06
Thanks for the tip but I guess it's something MainWin + Natty related.
Under Lucid (both x32 and x64) DxDesigner from EE7.9.2 works well but under Natty (both x32 and x64) is starts registering libraries and it takes a lot of time.
Surprisingly if I switch focus to another window and then back to terminal where DxDesigner was started it quickly advances for a couple more libraries registration.

I'll dive into Mentor and MainWin startup scripts to check what could be wrong.

---

### Post by cioma on 2011-07-23
Well, it looks there are a lot of futex timeouts occurring, perhaps when file lock is used. Has anyone seen this behavior?

---

