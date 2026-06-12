---
title: "Gnome Panel Settings Don't Stick"
date: 2006-10-17
forum: Desktop Environments
---

### Post by Tux Aubrey on 2006-10-17
If I uncheck the "expand" button (in the Properties dialog) for the bottom Gnome Panel it always appears at the top (under the top panel) after I reboot.  I cannot then use the Properties dialog to put it back at the bottom unless I recheck "expand" first.  

Ok, its just a minor annoyance, but is this actaully a "feature" of Gnome Panels (in the Microsoft sense of "feature"), is it a bug or is it perhaps just me?

I'd appreciate someone just trying this and letting me know.

---

### Post by mlnease on 2008-05-22
> **Tux Aubrey said:**
> If I uncheck the "expand" button (in the Properties dialog) for the bottom Gnome Panel it always appears at the top (under the top panel) after I reboot.  I cannot then use the Properties dialog to put it back at the bottom unless I recheck "expand" first.  

Ok, its just a minor annoyance, but is this actaully a "feature" of Gnome Panels (in the Microsoft sense of "feature"), is it a bug or is it perhaps just me?

I'd appreciate someone just trying this and letting me know.
Hi Aubrey,

I see your post is dated October of 2006.  Now it's May of 2008 and I'm still having the identical problem in Hardy (which is otherwise a delight).  Guess this isn't a big enough bug to bother with.

Cheers,

mike

---

### Post by vincentvee on 2008-06-03
> **mlnease said:**
> Hi Aubrey,

I see your post is dated October of 2006.  Now it's May of 2008 and I'm still having the identical problem in Hardy (which is otherwise a delight).  Guess this isn't a big enough bug to bother with.

Cheers,

mike

yeah i got the same problem, i fixed it, hit alt+f2 type gconf-editor got to apps on the left menu, then go to panel>toplevels>panel_0 you should have a value on the right called y_bottom which is set at -1 by default, what you should do is increse that value to a positive value, i used 10, that made my panel stick to the bottom when un-expanded.
good luck with it.....

---

### Post by malspa on 2008-07-03
Similar problems here with Hardy.  I uncheck "Expand" for the top and bottom panels.  When I start a new session, they have switched places, the panel I had at the top is at the bottom and the one I had at the bottom is at the top.

They will stay in their previous positions only if I check "Expand" before logging out.

Re: the post by vincentvee, in the Configuration Editor under app > panel > toplevels, I have bottom_panel_screen0 and top_panel_screen0, but no panel_0!

In Debian Etch's GNOME Configuration Editor, under app > panel > toplevels I DO have all three:  bottom_panel_screen0, panel_0, and top_panel_screen0.  And this problem with the panels switching does not occur in Etch.

Under top_panel_screen0 I have a y_bottom key that is set to 0.  If I change that value to 10, the top panel immediately moves to the bottom!

Can anyone help with this?  The GNOME panel issues in Ubuntu when they are not expanded are the only issues I am having.  Something like this also happens in Mint 4 (Daryna) but not in Etch.

---

### Post by mlnease on 2008-07-05
> **vincentvee said:**
> yeah i got the same problem, i fixed it, hit alt+f2 type gconf-editor got to apps on the left menu, then go to panel>toplevels>panel_0 you should have a value on the right called y_bottom which is set at -1 by default, what you should do is increse that value to a positive value, i used 10, that made my panel stick to the bottom when un-expanded.
good luck with it.....

VincentVee, yer a PRINCE.  Sorry for the delay, I haven't been back here since you posted this reply.

It worked, though my bottom panel is now on the top and vice versa.  I assume I can fix this just by reconfiguring the panels--at least now they stick.

Thanks a million!

mike

---

