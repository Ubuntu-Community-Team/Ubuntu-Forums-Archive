---
title: "xfce changed nautilus for thunar in gnome-panel"
date: 2011-05-11
forum: Desktop Environments
---

### Post by jperelli on 2011-05-11
Hello community!

I had gnome installed then I installed xfce4, I had both desktop environment working all right but, this was my problem:

In gnome desktop, in gnome panel all the folder links were opened with 'thunar', the default folder-browser of xfce, that included the places menu, and the recycler bin.

That was annoying, because I had many 'smb:\\' and 'sftp:\\' links in places that got good opened with nautilus and not with thunar, and also loaded thunar in memory, and nautilus was yet in memory.

So I searched in many places, I found some instructions using gnome-panel and others changing /usr/share/applications/... and so on. None of them worked for me.

Then looking around I could find a solution:
executed exo-preferred-applications and set the preferred browser as nautilus.

DONE!

So, my question is, what has this app (exo-preferred-applications) done?

thanks!:)

---

### Post by ManualSparrow on 2011-05-11
It just sets a default program for a given action - for example you can set a default browser, and any shortcuts using ```
exo-open --launch WebBrowser %u
``` will use whatever you specified as your default instead of a specific browser. There should be three or four options at least - mailreader, browser, terminal, and of course file manager. Never used it across windowmanagers though - check to see if Nautilus is the default in XFCE, too (it might be that they store that info seperately).

---

### Post by jperelli on 2011-05-15
Ok, I see, but I was thinking in searching the problem.
What kind of "preferred apps" use gnome-panel?
- those on gconf-tool?
- those on update-alternatives?
- those on exo-preferred-applications?

maybe that's a bug in gnome-panel, don't you think?

---

