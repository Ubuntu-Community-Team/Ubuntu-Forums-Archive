---
title: "Application window title bars hiding under panel."
date: 2012-01-16
forum: Desktop Environments
---

### Post by deeperDATA on 2012-01-16
I can't find anything relevant to this topic so here it goes.

I'm running Gnome fallback session with Compiz on Ubuntu 11.10. Sometimes when an application loads, the titlebar falls under the top panel leaving me to use keyboard shortcuts to move it or close it. It seems that some application windows do not dodge the panel or however you would say it. Any ideas on the fix?

---

### Post by kevdog on 2012-01-18
Sane thing happened to me.

Somehow my gconf settings and compiz settings became corrupt -- Too much mucking around.

Here is what I did:
cd ~
rm .gconf .compiz-1

Just a warning -- this removes all your settings.  I suppose its possible to first remove the .compiz-1 settings and see what happens. 

After I did this I had to go back into gconf-editor to change the max,min,close to the right side, and then headed back into the ccsm to configure compiz.  Didn't take too long.

Good luck.

---

