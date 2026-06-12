---
title: "X11 Forwarding small menus fonts"
date: 2009-10-02
forum: Desktop Environments
---

### Post by shaibn on 2009-10-02
[FONT=monospace]Hi,

When I start an X application in Gnome (My chosen XDM), the menus are just fine in relation to their font size. When I start those same applications later, on my Windows machine using SSH + X11 Forwarding, the menus fonts are very tiny and I can barely make the words for them... I was hoping maybe there is a way to change that?

Thanks in advance,
Shai
[/FONT]

**[COLOR=Red]Resolution:[/COLOR]**
[quote=Martin]If you don't have ~/.gtkrc-2.0, create it, containing the single line
> gtk-font-name = "geneva 12"Of course, you can choose different font names and sizes, but this is a good starting value.[/quote]

Reference: [http://lists.apple.com/archives/X11-users/2008/Mar/msg00164.html](http://lists.apple.com/archives/X11-users/2008/Mar/msg00164.html)

---

