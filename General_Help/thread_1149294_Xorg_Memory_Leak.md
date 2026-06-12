---
title: "Xorg Memory Leak?"
date: 2009-05-05
forum: General Help
---

### Post by Eneerge on 2009-05-05
I'm probably the only person seeing this, but I thought I would post anyway.  I've been seeing X consume huge amounts of memory.  As time passes, the memory consumption increases, which brings me to believe it's some sort of leak.  Here's the results of a few commands:
xlsclients : 25
xwininfo  : 295
top :
USER  |   PR   |   NI  | VIRT  | RES  |  SHR  | %CPU  |  %MEM  | TIME+  |  Command
root      20       0       1232m  764m  28m       2          19.6      7:07:24    Xorg

I keep having to restart X to free up this memory, because I think it would probably eventually fill up my 4 gigs within 8 hours or so.

Notice that when I launch a java applet in Firefox, memory for java goes up to 200megs (firefox stays around 90mb).  

What's the deal with all this crazy memory?

If anyone can help me figure this out, I'd appreciate it.

Thanks,

Evan

---

### Post by Eneerge on 2009-05-05
Here's a screenshot of the problem.[COLOR=Blue] ** It does not appear to be cache.**

EDIT: I just PROOVED it is NOT CACHE.
[/COLOR] 
I have also determined how to re-create the problem.  With effects enable, I simply maximize the window, then restore the window (de-maximize).  Each time the memory jumps up 25+mb.  If I continuously maximize/demaximize my memory will get this high.  I've also figured out that if I run other programs, opening/closing them will also increase the consumption.  The memory is never freed up.

[ATTACH]112556[/ATTACH]

Can anyone else reproduce this issue?

Xorg 1.6
Compiz
ATI HD4850
Kernel 2.6.28-10

EDIT:  It is definately a critical problem.  I just opened a few more programs and closed them and my entire system locked up.  Luckily I had DontZap disabled so a simple ctrl+alt+backspace restarted X (after a minute of waiting).  With a fresh Xorg process, my memory consumption is back down to 11% and 5% cache.

Filled a bug: [https://bugs.launchpad.net/ubuntu/+bug/372345](https://bugs.launchpad.net/ubuntu/+bug/372345)

---

