---
title: "Away with GNOME Panels! But 2 Problems with Cairo-Dock"
date: 2009-09-11
forum: Desktop Environments
---

### Post by Minipalmer on 2009-09-11
Hey guys,

I just made the move away from GNOME panels to work entirely off of Cairo-Dock, just for fun. I've got two problems with Cairo-Dock 2.0.8 (screenshot).

1. XMMS Plug-In won't freakin' go away. I've checked and unchecked it a hundred times, removed it from the dock, but it just stays there.

2. Cairo-Dock can't find a theme for the clock. Shouldn't this have been in the plug-ins package I installed? Can I find a new clock theme somewhere? I haven't had luck looking on gnome-look.org, everything is from a few years ago.

I'm on Ubuntu 8.10 Intrepid.

Thanks guys

---

### Post by fabounet on 2009-09-12
1/
maybe you have 2 times a same plug-in, look in /usr/lib/cairo-dock
look especially for gnome-integration or xfce-integration
if you have 2 times a plug-in with a similar name, delete one of it.
2/
themes are on the server, so you need to be connected.
a douzain of themes is available, and any Cairo-Clock theme can be used too.

---

### Post by Minipalmer on 2009-09-13
Thanks for the reply.

I don't see 2 of the same plug-in, but I do see the XMMS plug-in. Should I try to delete that?

How do I connect to the server? I've tried to find Cairo-Clock themes but I don't know how to install them.

Edit: I was able to remove the XMMS desklet by deleted the plug-in I found in /usr/lib/cairo-dock. Thanks. Now I just need to fix my clock.

---

### Post by fabounet on 2009-09-13
sometimes the server is down (like at the moment ...)
it usually doesn't last long.
you can place your own themes for clock in ~/.config/cairo-dock/extras/clock/your_theme
where "your_theme" is the name of your theme

---

### Post by Minipalmer on 2009-09-13
Thanks! I was able to toss some themes in and access them through the "module" tab of the desklet. Now I just have to find how to get a digital clock down there that I can see full-screen.

Edit: Found the digital clock. Was able to put a digital clock in the dock and an analog clock on the desktop. Looks great. Thanks.

---

