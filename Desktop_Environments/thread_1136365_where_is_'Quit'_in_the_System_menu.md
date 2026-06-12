---
title: "where is 'Quit' in the System menu?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by formol on 2009-04-24
hi, 

I tested 9.04 since alpha2, and, everything seems to be okay.  the debate around "ctrl-atl-backspace" vanished with time and resignation.

but, there is a really strange thing now and I hope it is a bug. 
there is no 'Quit' option in the System menu. 

is this normal??

------------------------------------------

apparently it's normal.  I try to re-add it with gconf-editor and didn't work, so I submit it to launchpad.

---

### Post by rozbarwinek on 2009-04-26
Yes, now it's only in the top-right all-in-one menu ;)

---

### Post by theozzlives on 2009-04-26
Use the fast user switcher and choose shut down.

---

### Post by mcduck on 2009-04-26
> **formol said:**
> hi, 

I tested 9.04 since alpha2, and, everything seems to be okay.  the debate around "ctrl-atl-backspace" vanished with time and resignation.

but, there is a really strange thing now and I hope it is a bug. 
there is no 'Quit' option in the System menu. 

is this normal??

------------------------------------------

apparently it's normal.  I try to re-add it with gconf-editor and didn't work, so I submit it to launchpad.
Instead of Ctrl-Alt-Backspace use Alt-SysRq-k, if you need to.

And like others already pointed out, the shutdown options are now only in the user switcher-applet. However if you remove that applet from your panel the shutdown options will appear in the System menu again.

---

