---
title: "[ubuntu] black screen and cursor only after log in"
date: 2014-02-25
forum: Desktop Environments
---

### Post by btc2 on 2014-02-25
Ubuntu 13.10

Worked until today. Restarted computer and now my desktop is a black screen, no icons, and all i have is the cursor. 

I _**AM**_ able to log in with the guest account and view everything fine. 

When I run unity, I get
> Invalid MIT-MAGIC-COOKIE-1 keycompiz (core) - Fatal : couldn't open display :0

unity --reset gives me a warning/error. 


Any help on how to fix this? Doesn't seem to be a drivers issue. Again, I'm able to get the log in screen and full function of the guest account.

---

### Post by JanneM on 2014-02-25
I seem to have something very similar: restarted after the updates yesterday, and now I get a black screen and the cursor only. The lightgdm login screen works fine. 

In my case, though, the guest account doesn't work either; I get he same black screen there. Could be because I use dual monitors, and whatever issue is triggered for the guest account as well?

If I boot with the slightly older kernel 3.11.0-15 I no longer have a black screen; I get my background and can open terminals with ctrl-alt-T but I have no window decorations of any kind. If I try guest session at this point I get a normal working desktop.

Could it possibly be that the kernel got updated but the NVIDIA drivers did not?

---

### Post by JanneM on 2014-02-26
I "fixed" it for myself by reverting back to the nouveu drivers. They work well enough for me anyhow, as this is a work machine, not for games.

But I realized you can get around this by booting the older kernel. You get a desktop but no menus or window decorations, but that's because unity got disabled in compiz settings. To fix it:

* Press ctrl-alt-t to get a terminal.
* Run 'ccsm'
* enable the opengl plugin (near the top) and the 'Ubuntu Unity plugin' further down.
*  When it complains about duplicate keybindings, tell it to ignore (or  disable, I forgot which); it's likely not important either way.

If you can get a desktop by booting the older kernel, that should do it for you until a further update fixes this issue.

---

