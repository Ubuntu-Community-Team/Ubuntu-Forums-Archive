---
title: "xfwm4 and gnome logout"
date: 2007-11-06
forum: Desktop Environments
---

### Post by alvinistic on 2007-11-06
Hello all,

I replaced metacity with xfwm4 to gain a simple and stable compositor without the whiz-bang like compiz fusion. Everything went well so far except for one thing: it always hangs when there is a prompt with darkened background. This includes the password input prompt (but I can just disable-grab from gconf-editor, so no issue here) and the logout.

Is there any workaround to get the logout prompt working? Thanks.

PS: It works if I turn off the compositor.

---

### Post by thomasvm on 2007-11-07
Hi alvinistic,

I'm experiencing the exact same problem since the upgrade to gutsy, it used to work before.  I've tried editing the /usr/bin/gnome-wm script to pass the correct parameters onto xfwm4 but i didn't succeed in fixing it.

So anyone managed to fix this?

---

