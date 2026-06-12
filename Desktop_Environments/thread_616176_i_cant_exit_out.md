---
title: "i cant exit out"
date: 2007-11-17
forum: Desktop Environments
---

### Post by darksora145 on 2007-11-17
when i start up firefox, and all other programs. Like it shows the minimize, and x to exit out. Well when I restarted i cant see it anymore. Its like stuck to the top. and know how to fix it?

---

### Post by Diabolis on 2007-11-17
The problem is related to the window manager, try typing this in the terminal: metacity --replace.

---

### Post by darksora145 on 2007-11-17
omg thanks :DD

---

### Post by darksora145 on 2007-11-17
crap now none of my effects work after that. Also XGL lags everything up. So after i deleted it. Everything was back to normal. I use a regular MACBOOK i think its the second gen with 1 gig memory

---

### Post by tyggna1 on 2007-11-17
Yeah, metacity is a less-eye-candy window manager that is much more stable.   Your problem was with the window manager and the software you wanted to use.   I'd report a bug on bugzilla.

---

### Post by darksora145 on 2007-11-17
so is there a way to fix this? or do i have to post up a bug?

---

### Post by tyggna1 on 2007-11-17
I'd check to make sure that the right driver is being used for the card.

If you didn't have that problem before--then you could try typing in:
```
sudo dpkg-reconfigure compiz
```
and then doing the same --replace command, only with compiz instead of metacity.

I have problems with beryl on my computer too--it's just not as stable as metacity, and those developers need to know which bugs to work on--so I'd still file a bug report, in either case.

**note:  what you put in on the replace and the dpgk-reconfigure depends on what window manager you had before, so if you use beryl, type in beryl.

---

