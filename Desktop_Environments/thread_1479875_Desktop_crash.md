---
title: "Desktop crash"
date: 2010-05-11
forum: Desktop Environments
---

### Post by novice buntu on 2010-05-11
Hi,

My desktop has suddenly refused to load. I had applied some updates last week. My PC worked fine on Sunday but on Monday when I booted it the system froze at the point where the login screen should appear. The keyboard does not respond to Caps-lock or Crt-Atl-{Del,Backspace}. I can boot into recovery-mode but once I startx I get the same probem.

If I use a slightly older kernel and try to startx I get the desktop backup-ground colour but nothing else, no mouse cursor or menus.

I can't find any problems reported in the logs. Can anyone give me some trouble-shooting tips or have any idea on what I might be able to do?

Sorry if I am short of details but I have to write this from work now that the desktop is dead and I don't have all the details to hand. 

Can anyone offer any pointers? 
Thanx,
Dp.

---

### Post by 3rdalbum on 2010-05-11
> **novice buntu said:**
> The keyboard does not respond to Caps-lock or Crt-Atl-{Del,Backspace}.

Control-Alt-Backspace does nothing these days. Try Alt-PrintScreen-K to kill the X server when the login screen should be appearing. The Printscreen key is sometimes labelled "Pr Sc" or "SysRq".

---

### Post by novice buntu on 2010-05-11
I'll try but I think, as the caps-lock light doesn't come on, that all keyboard activity is going to fruit-less once I get to this point.
Dp.

---

