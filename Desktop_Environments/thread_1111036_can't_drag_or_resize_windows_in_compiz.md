---
title: "can't drag or resize windows in compiz"
date: 2009-03-30
forum: Desktop Environments
---

### Post by miatawnt2b on 2009-03-30
I have no idea what's going on.  I rebooted this morning, and all of a sudden I couldn't select anything with button 1 on the mouse. If I held button 1 over a window, it would allow me to move the window just as if I'd click and hold on the window's title bar.  I figured something must be wack with compiz, so I replaced the window manager with metacity, and everything is normal, confirming my suspicion. 

So I restarted compiz and opened compizconfig settings manager and tried to find what was messed up.  I did find a plugin called "move window" which had button 1 enabled, so I disabled the plugin.  This returned my button 1 to allow me to select things like radio buttons, but I could no longer move windows using the title bar, nor could I resize.  At this point I think I am at a loss.

What am I missing?

-J

---

### Post by serge_8766 on 2009-03-30
You should enable "Move Window", but you should modify it.
Inside the plugin, set "Initiate Window Move" to <Ctrl><Alt>Button1.
Also enable "Resize Window".
Inside the plugin, in the bindings tab, set "Initiate Window Resize" to <Ctrl><Alt>Button2.

---

### Post by NewUserFF on 2012-02-18
> **serge_8766 said:**
> You should enable "Move Window", but you should modify it.
Inside the plugin, set "Initiate Window Move" to <Ctrl><Alt>Button1.
Also enable "Resize Window".
Inside the plugin, in the bindings tab, set "Initiate Window Resize" to <Ctrl><Alt>Button2.

Oh, thx, i googled to here, and what you suggested works for me. Great!

---

