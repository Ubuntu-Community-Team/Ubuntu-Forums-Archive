---
title: "Mouse Click Event Issues with Compiz"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Der Eroberer on 2009-10-30
Hi,

I've got 9.10 running on a Dell Inspiron 1520 (Intel GFX). A problem I have encountered which seems tied to Compiz being enabled or disabled is the capture of mouse clicks.

Under Compiz enabled the YouTube video player for instance acknowledges mouse hover but doesn't mouse clicks; if I right click on play/pause the mouse icon actually changes so Ubuntu is picking up the event but doesn't seem to be passing it on. If Compiz is disable I don't see the problem.

I also see this when using Eclipse 3.5; if I am installing something in Eclipse right click highlights/toggles the button, but subsequent clicking doesn't pass onto the command button - very odd. Maybe it's a underlying Gnome issue?

Anybody had these issues? I see a few bugs submitted in relation to the YouTube problem, not many people may have picked up on Eclipse click problems yet - probably likely the issue is with Java's GUI rendering tie ins with Gnome not Eclipse IDE specific - but it is the only Java app I run.

Thanks!

---

### Post by Adrian Challinor on 2009-12-08
Yes - exactly the same. Eclipse does not recognise the mouse. You can select a dialog button, but the actual click is not passed to the dialog event loop. 

SOLVED - disabled the Compiz "Mouse Polling Position" and I have Eclipse back. 




> **Der Eroberer said:**
> Hi,

I've got 9.10 running on a Dell Inspiron 1520 (Intel GFX). A problem I have encountered which seems tied to Compiz being enabled or disabled is the capture of mouse clicks.

Under Compiz enabled the YouTube video player for instance acknowledges mouse hover but doesn't mouse clicks; if I right click on play/pause the mouse icon actually changes so Ubuntu is picking up the event but doesn't seem to be passing it on. If Compiz is disable I don't see the problem.

I also see this when using Eclipse 3.5; if I am installing something in Eclipse right click highlights/toggles the button, but subsequent clicking doesn't pass onto the command button - very odd. Maybe it's a underlying Gnome issue?

Anybody had these issues? I see a few bugs submitted in relation to the YouTube problem, not many people may have picked up on Eclipse click problems yet - probably likely the issue is with Java's GUI rendering tie ins with Gnome not Eclipse IDE specific - but it is the only Java app I run.

Thanks!

---

