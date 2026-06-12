---
title: "XGL/Compiz - all programs disappear from workspace?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by chucknorris on 2006-08-02
This happens from time to time and is just annoying. The programs are still running but somewhere outside the workspace!

I run the XGL/Compiz installation described in [http://ubuntuforums.org/showthread.php?t=222034](http://ubuntuforums.org/showthread.php?t=222034) . 


Any help would be appreciated! Thanks

---

### Post by emax on 2006-10-11
I've also experienced this.

It seems to be a random thing.  Sometimes you can get the window(s) to re-appear by switching back and forth between workspaces but it doesn't always work.

Expose (working across all desktops shows a preview of the missing windows (<F10).

Also, desktop switching across all desktops also shows them <CTRL><ALT><TAB>.

What I end up doing when this happens is revert to metacity with:

> 
metacity --replace &


Edit:  I should perhaps also mention that I'm running AIGLX, not XGL, so it looks like the problem is Compiz-specific.

---

