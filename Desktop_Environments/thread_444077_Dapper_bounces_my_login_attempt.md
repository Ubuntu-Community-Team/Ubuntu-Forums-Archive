---
title: "Dapper bounces my login attempt"
date: 2007-05-15
forum: Desktop Environments
---

### Post by crossedout on 2007-05-15
Hi folks,

I was recently trying to edit the font color for my clock applet with no luck.  Then I stumbled upon a piece of code that would do the trick when placed in the /home folder:

```
style "panel-clock"
{
  fg[NORMAL] = "#FFFFFF"
}
widget "*.clock-applet-button.*" style "panel-clock"
```

Well, now when I attempt to login, I am immediately bounced back out to the login screen.  It only affects the login I tried it in and removing the file did not correct the issue.  Using recovery mode yields the same result.  I am at a complete loss on how to fix this, can anyone offer some advice?

-Xout

---

### Post by crossedout on 2007-05-15
For those who may run into a similar problem, I resolved the issue by:

-Using failsafe terminal
```
gconf-editor&
```

Navigate to apps->panel->applets and find the clock-applet.  Find the entry for toplevel_id and unset the key.
It essentially removes the applet from the panel, allowing for proper login.
If anyone has ideas on why the original issue occurred, I'd be appreciative to have it explained to me.

Thanks,
-Xout

---

### Post by crossedout on 2007-05-15
Well, the problem refuses to go away completely.  It is now intermittent.  It takes usually 3 or 4 login attempts before I can actually get in.  The error seems to fluctuate between the original "time" applet and the others, usually located on the right side of the panel.

I reloaded .gconf &.gconfd back to the default but that didn't cure the problem.  I am additionally receiving an error from my monitor stating that it is "out of range" (but again intermittent).

I plan to install FF soon but had planned on keeping my separate /home partition.  Now I have a feeling I'll have to do a complete format/reinstall.
Does anyone have any idea how I can revert or disable or bypass or ignore the code previously entered?

Thanks,
-Xout

---

