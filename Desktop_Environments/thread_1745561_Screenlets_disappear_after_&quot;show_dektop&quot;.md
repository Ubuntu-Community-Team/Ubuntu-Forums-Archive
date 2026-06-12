---
title: "Screenlets disappear after &quot;show dektop&quot; command"
date: 2011-05-01
forum: Desktop Environments
---

### Post by ilpiero on 2011-05-01
Hi all.
I've just installed Ubuntu natty, and I'm using the good old classic interface.
I found that the Screenlets disappear when I press show desktop.
This is a known issue :

[http://www.screenlets.org/index.php/FAQ#Why_do_my_screenlets_disappear_when_I_show_the_desktop.3F](http://www.screenlets.org/index.php/FAQ#Why_do_my_screenlets_disappear_when_I_show_the_desktop.3F)

[http://ubuntuforums.org/archive/index.php/t-533951.html](http://ubuntuforums.org/archive/index.php/t-533951.html)

but the solutions don't seem to work anymore.

Is anybody facing the same problem?

Thanks

---

### Post by GaryParr on 2011-05-03
I'm experiencing similar issues with a terminal window I keep transparent and stuck to the desktop. My guess is that gnome is not honoring the hide_skip_taskbar_windows setting for some reason.

---

### Post by ilpiero on 2011-05-06
Unchecking "hide skip taskbar windows" in the compiz config setting manager (general section) seemed to solve the problem.

---

### Post by GaryParr on 2011-05-12
> **ilpiero said:**
> Unchecking "hide skip taskbar windows" in the compiz config setting manager (general section) seemed to solve the problem.

BAH!  Yep, that does it.  I was setting flags directly in gconf editor.

---

### Post by treasonvoice on 2011-05-12
I love the fact that I can find a fix for an annoying little half-bug and not really know why it works. Gotta love Ubuntu.

---

### Post by haikalpribadi on 2011-09-14
I wonder why the solution doesn't work on me. Does anyone else have any idea? 

Cheers guys..

---

### Post by haikalpribadi on 2011-09-14
oh i found the solution! so, for anyone who's have the same problem, that has Unchecked "hide skip taskbar windows" in the compiz config setting manager (general section) but the screenlet still disappears:
1. Unchecked "hide skip taskbar windows" in the compiz config setting manager (general section)
2. go to the 'window rules' in compiz config setting manager (Window Management)
3. add the parameter to identify the window type to skip taskbar in the "Skip Taskbar" field: "type=toolbar" or "name=whatEverScreenlet.py", without the quotation marks.

Cheers

---

