---
title: "Default window manager on login"
date: 2009-11-25
forum: Desktop Environments
---

### Post by oldmankit on 2009-11-25
This question has been asked a few times but I'm yet to see a satisfactory solution.  Forgive me if I haven't understood the concepts properly...

I want compiz to run on login as the default window manager.  I can make it start easily using 'exec compiz' but that's very clumsy as a permanent solution.  Slightly less clumsy is to add a startup script that will do that, but that is bloated.  It means running a different window manager on login, and then replacing it with compiz. 

Here's what I've tried (following the advice of others).

Adding ~/.gnomerc.  Contents here:
```
export WINDOW_MANAGER=/usr/bin/compiz
```

This had no effect.

Next I tried creating .xinitrc  .xsession in my home folder.  The contents of both:
```
exec compiz
```

Still no luck.  This should be super simple and well documented.  What am I doing wrong?

---

