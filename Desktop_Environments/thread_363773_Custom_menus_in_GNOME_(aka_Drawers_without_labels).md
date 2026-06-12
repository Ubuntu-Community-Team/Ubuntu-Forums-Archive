---
title: "Custom menus in GNOME? (aka Drawers without labels)"
date: 2007-02-17
forum: Desktop Environments
---

### Post by gumpish on 2007-02-17
Hi.

I'm running Ubuntu Edgy (default GNOME version) and have encountered a bit of a snag in setting up my desktop environment.

Specifically, what I want is a menu containing application launchers which I create and organizing them in a highly accessible fashion. The GNOME solution for user-generated menus is Drawers. Unfortunately there appears to be what I consider a critical feature missing from Drawers. Namely the items you add to a drawer only appear as an icon (and a tooltip if you hover over them) and **DO NOT HAVE LABELS.**

To illustrate the problem, I routinely SSH into several hosts throughout the day. So I created a drawer and began populating it with custom application launchers, one for each host I connect to. I named the connections in the "comments" field, chose the same icon for each one, and closed the configuration panel. What I got was a column of icons with NO labels and my names for each connection only appeared as tooltips.

So in order to differentiate the connections, I either have to mouse over each one to find the one I'm looking for, memorize the position of each connection, or give each connection an arbitrary icon and try to make some mnemonic association in my head.

I don't find any of those workarounds acceptable. I checked the Help file but it didn't give me any information about hacking a conf file somewhere to get this basic functionality...

Is there a way to get drawers to display labels, or is it only an icon-based tool?

Does Xfce offer customizable menus? I know Window Maker does, and I suspect Window Maker is where I'll end up...

Thanks

---

### Post by gumpish on 2007-02-17
It appears that this behavior is intentional and labels were removed from GNOME 1.x per the following post to the GNOME mailing list in 2004:

[http://www.arcknowledge.com/gmane.comp.gnome.general/2004-05/msg00060.html](http://www.arcknowledge.com/gmane.comp.gnome.general/2004-05/msg00060.html)

Sadly the only reply to that message was very sarcastic and essentially says "no one forced you to switch to GNOME 2."

Guess I'll join the GNOME forum and see what the community there has to say today.

---

### Post by paparucino on 2007-02-17
> **gumpish said:**
> Hi.
I don't find any of those workarounds acceptable. I checked the Help file but it didn't give me any information about hacking a conf file somewhere to get this basic functionality...

You could try System -> Gnome Control Center -> Main menu
or run alacarte which is the same thing.
It allows you to create menu, add items with comments.

---

