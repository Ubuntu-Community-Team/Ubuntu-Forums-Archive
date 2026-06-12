---
title: "Pointer grab freeze bug (gnome?)"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Alex1770 on 2006-09-12
Every now and again (about three times a day) my desktop becomes unusable because the mouse pointer won't turn back into a pointer (little arrow pointing up and left) - it just stays as the text-input shape (like a capital I with serifs).

This seems to be provoked when I click in a window or try to select something by click-and-dragging in a window. I thought it was firefox at first, but then it happened with other windows too. I think it's as if the application running in that window does an XGrabPointer and doesn't let go, though it isn't likely to be the fault of the application since it happens with different applications.

If you log in remotely (or use CTRL-ALT-F1 or something to get a text login) and kill the relevant window (the one that was clicked in which caused the problem), then the pointer resets itself back to normal.

In case it's relevant/helpful:
I have a clean install of Dapper with all the updates on a AMD XP 2400+. In the Device section of /etc/X11/xorg.conf it says                  
```

        Identifier      "Matrox Graphics, Inc. MGA G400 AGP"
        Driver          "mga"
        BusID           "PCI:2:0:0"
        VideoRam        32768
        Option          "OldDmaInit"            "True"

```
and the loaded modules in xorg.conf are bitmap, ddc, dri, extmod, freetype, glx, int10, type1, vbe.

I can't find anything in any log file (~/.xsession-errors, /var/log/*), and the bug is not predictable (I don't know how to provoke it).

I wonder if anyone has any suggestions. I couldn't find this bug reported anywhere else (though it is a bit hard to search for because it isn't obvious how to describe it concisely). Thanks in advance.

---

### Post by chownrus on 2006-09-14
Same problem here. I thought it was firefox, as well.

---

### Post by Alex1770 on 2006-12-14
I'm still getting this problem (Curiously, less often though. Perhaps the general updates have somehow improved it). I've noticed there is a workaround: pressing Alt-Tab when it is stuck appears to unstick it. It seems the problem was that the focus was frozen, and no amount of mouse moving or clicking would unfreeze it, however Alt-Tab is a keyboard shortcut to change the focus.

I'm using focus-follows-pointer (System->Preferences->Windows, Select windows when the mouse moves over them). Perhaps the problem is related to this.

---

### Post by Magneto on 2007-06-14
Same problem here. There is a bug registered for this but no fix posted there works for me. Along with this problem I get terrible key repeats so now copy and pasting into a terminal while using gnome is more important and this stupid focus problem will lock me up when attempting to switch between apps without grabbing or other functions. Grabbing will actually lock my system up for a minute or two but switching between gnome and a terminal will stop it.

---

