---
title: "KDocker at system startup in GNOME"
date: 2008-08-04
forum: Desktop Environments
---

### Post by Twilight in Zero on 2008-08-04
Hi, I'm having some issues running KDocker at system startup. I'm using GNOME. I have two entries in my sessions for Thunderbird and a Gnome terminal. They are "kdocker thunderbird" and "kdocker gnome-terminal" respectively.

But at system startup, I get this dialog that says, "System tray appears to be hidden". Actually, two of them. One over the other. The programs won't load until I click "Ignore" on them. Interestingly, if I log out and log back in, this doesn't happen.

Is there any way I can work around this? Maybe with a script or something? It's annoying having to click those dialogs away each time.

---

### Post by Twilight in Zero on 2008-08-04
I actually ended up making scripts that would wait a few seconds, and then load the programs.

And then I found an updated version of AllTray in this thread: [http://ubuntuforums.org/showthread.php?t=764557&highlight=alltray&page=2](http://ubuntuforums.org/showthread.php?t=764557&highlight=alltray&page=2)

I originally didn't use AllTray because it didn't work for me, at all. But now it works better than KDocker, at least for me. The window doesn't even appear before hiding like in KDocker. And the close button works properly now too.

---

