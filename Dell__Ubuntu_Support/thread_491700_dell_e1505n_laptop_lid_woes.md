---
title: "dell e1505n laptop lid woes"
date: 2007-07-03
forum: Dell  Ubuntu Support
---

### Post by crazedgremlin on 2007-07-03
ok here's the story:
1.  Ordered the e1505n (intel graphics).
2.  It came in the mail.
3.  Opened it up.
4.  Worked fine.
5.  Erased disk and installed kubuntu.
6.  I told guidance power manager (the default battery thingy) to suspend when I put the top down.

Problem: It worked partially; sometimes I would put the top down and it would suspend just like that, other times I would put it down and it didn't work at all.  I thought it was probably a bug in guidance, so I replaced guidance with kpowersave....  same problem!

Can anybody tell me what's going on?

---

### Post by neptho on 2007-07-04
I have the same issue; it worked for the longest time, but after a sleep, I have to manually sleep it.

Since I can right click on "Power Manager" and choose "Suspend", I haven't bothered to investigate further.

---

### Post by neptho on 2007-07-04
Followup: I installed and ran kpowersave rather than the kde-guidance-powermanager applet that Ubuntu has.  I re-configured that, and now it's sleeping properly.  5 out of 5 times, it went to sleep.

So, that's:
```
%sudo apt-get --purge remove kde-guidance-powermanager
%sudo apt-get install kpowersave
```

Then, of course, run KPowersave in K->System->KPowersave (or from the command line).

Hope that helps you as well.

---

### Post by crazedgremlin on 2007-07-04
yeah I'm using kpowersave now but it still has the same problem.  I was wondering this morning if it's a mechanical problem - when I close the lid and watch the screen I see the screen go dark, but then when it closes all the way I can see that the screen turns back on.

Is that normal?

---

### Post by cody50 on 2007-07-04
why did you have to erase it? couldnt you just install kubuntu-desktop?

---

### Post by neptho on 2007-07-04
> **crazedgremlin said:**
> yeah I'm using kpowersave now but it still has the same problem.  I was wondering this morning if it's a mechanical problem - when I close the lid and watch the screen I see the screen go dark, but then when it closes all the way I can see that the screen turns back on.

Is that normal?

No, it's entirely software controlled.

Since that hasn't taken care of this issue for you, I'd suggest the 'right click, suspend', which I have been using, and file a bug report on [LaunchPad](http://launchpad.net).  :)

I have counted no less than THREE different places with the default KDE installation to manage this:

**K->Settings->Power Control**
**Power Manager Applet**
and finally, my own installation of **kpowersave**.

You might look for 'warring' different versions of these applications; they might be trying to fight to see who wins, and catching a condition wherein the system decides "Ok, fine, I'll stay awake.  Sheesh!"  ;)

---

### Post by crazedgremlin on 2007-07-04
> **cody50 said:**
> why did you have to erase it? couldnt you just install kubuntu-desktop?

because I thought that there were 'warring' (quoting neptho) bits of software.

@neptho: thanks that's what I'll be doing.  On launchpad I found many similar bugs that were submitted but they all seemed to apply to gnome power manager.  I'll get around to submitting a bug in the next few days.

---

