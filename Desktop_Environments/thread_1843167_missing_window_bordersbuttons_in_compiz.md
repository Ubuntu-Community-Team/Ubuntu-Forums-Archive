---
title: "missing window borders/buttons in compiz"
date: 2011-09-13
forum: Desktop Environments
---

### Post by karrank% on 2011-09-13
I don't have good search fu, so apologies if this has been asked before. 

I'm running 10.04 (yes, still) and I like compiz & the cube but it seems unstable in the sense that my window borders and buttons have gone missing-- rather not have to go back to metacity. Can someone tell me where to start looking for a solution? 

Thanks for looking.

---

### Post by BlacqWolf on 2011-09-13
May I ask which desktop environment you are running? 

Also, you may see if an update to Compiz or your desktop environment is available which may fix the issue. You may also be using certain Compiz features that are unstable, or the settings have been corrupt, causing this issue. Therefore, it may help to reset Compiz settings and try customizing again.

Open a terminal, enter the following text, and reboot.

*sudo gconftool-2 --recursive-unset /apps/compiz*

If this fixes it, you may also try enabling features you were using one at a time to see which one may be causing the issue.

---

### Post by ramire on 2011-09-13
check the "window decoration" in compizconfig

---

### Post by psrdotcom on 2011-09-13
After performing the restart, does it still having the problem?

---

### Post by karrank% on 2011-09-13
Thanks for looking folks. Love this community.

BlaqWolf, --emerald. I have metacity if I want to enable it as well.

Will try your terminal tip and respond by day's end.
 
ramire -- already checked that, done.

psrdotcom --yes, problem, perversely, persists.

---

### Post by karrank% on 2011-09-13
> **BlacqWolf said:**
> 

Open a terminal, enter the following text, and reboot.

*sudo gconftool-2 --recursive-unset /apps/compiz*



terminal command doesn't appear to do anything, no indications at all of any activity-- just sends me back to terminal prompt.


??

---

