---
title: "AWN and panels"
date: 2013-02-24
forum: Desktop Environments
---

### Post by JiuJitsu500 on 2013-02-24
So, once again I'm finding something simple I can't seem to get to work.

I bought the other half an Acer laptop a while back (P200, 4GB 1333 RAM, not a bad little work machine) and was convinced to get rid of the GNOME 3 desktop - I guess she changed her mind about the shell and the fallback all the sudden, and likes unity but loves her mac.

So, I decided xubuntu would run like a boss on this thing and war far from wrong - it's been the smoothest experience I've had since Lucid on any laptop, with any distro, or any remix. I'm almost convinced to switch to it later.

Anyway though, the meat of my issue. I got rid of the bottom panel they made look and feel kind of like a dock and replaced it with an actual dock with AWN (I remember loving this back in karmic days).

I know how to remove the top panel too, but I can't yet since she doesn't like the CTRL+ALT+<left, right, up, down> to navigate a workspace nor remapping it to a simple SUPER-direction. She, and i , like a preview for them but both AWN's switcher don't work, and neither show a preview...

Anyone else have a fix for this? I can change I suppose to Docky or Cairo, but AWN is light and fast and looks a little better than docky...

The only thing stopping the removal of the top panel is that switcher.

---

### Post by LewisTM on 2013-02-24
You cannot easily remove all Xfce panels, they are bound to the Xfce session. You can make a single panel as small as possible, to hold things like the indicators and notification icons, and make it autohide.

If you plan on upgrading any time in the future, I would recommend you go with Cairo. AWN is no longer being developed and has been removed from the 12.10 repos. Cairo also doesn't bring in GNOME dependencies like AWN does.

Cheers!

---

### Post by Frogs Hair on 2013-02-24
There is a newer AWN PPA for installation, but may not be fully functional due to lack of updates. So, though you can install AWN is still dead in the water.

---

### Post by JiuJitsu500 on 2013-02-25
Okay, cool beans.

I looked around some, and yeah you both were right. AWN is dead. I'm onj 12.04 too so I thought maybe something good might be hanging around. It's still functional and looks good, but screw it if it's not under development still.

If I'm not mistaken too, the panel scan be removed from autostart or through commenting out the xfce4-panel option ---/xfconf/....something.../xfce4-session.xml.... but then again that's an older trick i think (haven't used xfce and ubuntu together in a long time so I might be wrong).

~/.config/xfce4/autostart.sh in here placing a few lines should do it too, but that's kind of no bueno and might screw something else up.

And like you said, dependencies come up so yeah...

Cairo it is then, maybe docky. We'll see. Thanks again!

---

