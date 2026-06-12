---
title: "XDM resolution"
date: 2007-08-28
forum: Desktop Environments
---

### Post by Underpants on 2007-08-28
pc starts up and comes to xdm @ 1280x1024, and I log into xubuntu and it changes to 1024x768 (where I want it)

This is a machine that I'm never near, and it has x11vnc running in the xdm startup script. so when I log in, it goes to XFCE and the resolution changes, and messes up vnc so I can't connect..

how do I edit the resolution on xdm to match what XFCE uses?

---

### Post by mcduck on 2007-08-29
You could just remove all the other resolutions from /etc/X11/xorg.conf. After that XDM should use the resolution you want.

---

### Post by Underpants on 2007-08-29
> **mcduck said:**
> You could just remove all the other resolutions from /etc/X11/xorg.conf. After that XDM should use the resolution you want.

That's what I ended up doing. Sometimes I'll want everything to be a 1280x1024, but it's so rare I'll just manually edit and restart x.

---

### Post by krunge on 2007-09-01
> This is a machine that I'm never near, and it has x11vnc running in the xdm startup script. so when I log in, it goes to XFCE and the resolution changes, and messes up vnc so I can't connect..

Not sure what "messes up" means.  The x11vnc process is no longer running, or something else?

Try the x11vnc -xrandr option and see if that helps.

---

