---
title: "Changing the look of nautilus"
date: 2008-01-18
forum: Desktop Effects &amp; Customization
---

### Post by wheezer on 2008-01-18
Being fairly new to Linux, I still prefer using Nautilus for most file browsing.

I use a "pseudo-nautilus" script to launch it as root user when i need to do system stuff.

But I have two annoyances with it:

1) having to enter password each time.  Can I force this in the script below?

2) The look and feel of the window is identical to non-root nautilus, which results in confusion at times.  Can I somehow alter the titlebar color, window colors, or some other visual element for the root nautilus launched by this script below (even if it calls some other config script?)  ANYTHING that can make it distinct from a normal user version?

Thanks

==== PSEUDO NAUTILUS SCRIPT ====================
#!/bin/bash
# Opens a nautilus window as root.

foo=`gksudo -u root -k -m "enter your password for nautilus root access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI

---

### Post by FuturePilot on 2008-01-18
I'm not quite sure about the password part, but if you set a theme that you installed yourself, the root nautilus window will look completely different since your own themes are not applied system wide. Only the default themes are.

---

### Post by wheezer on 2008-01-19
Hmm.. so you are suggesting my_name have one theme, and root another?  That's logical. Can I do that.  Lemme try.

Wait.. i haven't a clue. I can only login to root from terminal.  How would I do this?

---

