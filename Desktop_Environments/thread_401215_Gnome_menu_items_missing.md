---
title: "Gnome menu items missing"
date: 2007-04-04
forum: Desktop Environments
---

### Post by Ndlovu on 2007-04-04
I have a *lot* of menu items missing from my Applications and System menus after upgrading from breezy to dapper. For example, 'Synaptic' and 'Users and Groups' are both missing from the System menu, although I can still load them from the terminal.

I have looked in Alacarte, and the required menu items all have a tick mark next to them so they should be visible. I've tried unchecking all menu items and rechecking them again, but still only a handful show up in the menus.

Any ideas what could be the problem, or alternatively how to rebuild the menu structure?

Thanks,
Rudi

---

### Post by rillip on 2007-04-04
Not sure if this is related or not, but I had a similar issue happen with KDE.

What happened with me:

Long story short, my hard drive got over filled.  I went to a recover session and was able to free up enough space to reconfigure xserver-xorg.  With that done, the gui was able to load.  

However, I noticed my sound was not working for some reason.  When I went to the ultimate sound guide, part of the instructions required a reboot.  That's when I found that many of my buttons were gone - all the programs I'd installed were missing, the shutdown options were missing, even though everything seemed checked, just like you.

Eventually with some hard work and tinkering (and a lot of trial and error; read, I'm not exactly sure), I manged to kill my old session and start a fresh one.  It seems that when I went into the recovery console, which I think is a single-user-mode, the session had gotten saved and was being loaded when I went back in.

So I think I would recommend a) starting a new session and see if it's there
b) starting a  new session, killing the old one, and rebooting
c) rebooting, and from the login box see if you can keep from restoring the old session this time, maybe by going to console and runing startx as your user, maybe just restart xserver from there, etc.

No guarentee that if you do get into a new session that it'll work, but it did for me.  And since you just upgraded, I can see a similar sort of thing having happened.  Good luck!

---

### Post by Ndlovu on 2007-04-04
Something you said definitely rings true here. My hard drive was also filled to capacity during the upgrade. I managed with quite a bit of effort to get everything working again, and now it seems that it's only this issue that's left to resolve (I hope!!). 

> So I think I would recommend a) starting a new session and see if it's there
b) starting a new session, killing the old one, and rebooting
c) rebooting, and from the login box see if you can keep from restoring the old session this time, maybe by going to console and runing startx as your user, maybe just restart xserver from there, etc.

I've tried these suggestions but it still seems to be doing the same thing. The other thing that makes me suspicious is that I can use alacarte to change the order of the menu items. Items that are already visible stay visible but change their order. Items that are currently invisible (though selected) remain invisible. The point here is that the menu structure and session is responding in some way to my settings.

But the similarities in what you say are making me wonder... At any rate, thanks for your reply. I'll ponder it some more and try some other session manipulation tricks!

---

### Post by mr.propre on 2008-07-13
well, this is kind of old but still a problem. Is there a way you can rebuild the gnome menu?

---

