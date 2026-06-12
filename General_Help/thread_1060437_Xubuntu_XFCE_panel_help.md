---
title: "Xubuntu XFCE panel help"
date: 2009-02-04
forum: General Help
---

### Post by Culgan on 2009-02-04
Alright, so this question is gonna sound pretty newbish, but I'd rather not mess with this further and dig myself into a hole I can't get out of so..

Okay, so running Xubuntu Hardy Heron i386 version, and I can't get my "taskbar" aka XFCE panel to look the way I want it. I messed it up a lot more than it was. I want it to stretch across the whole bottom of the screen so that the Applications and Places menu are way on the left, and the clock on the right. I can only move the entire panel around, but I can't stretch it. Here's what it looks like now:

Nevermind, I can't even do a print screen, nothing happens. 

Okay so from left to right it goes:

Open programs such as Firefox and Pidgen, then Applications and Places menu, then Firefox and Help shortcuts,  then the little lightbulb, then to the right of that is the "system tray" with the Pidgen icon, then the clock.

I want it to go:

Applications Menu, Places, Firefox and ? shortcuts, "System Tray", open programs, then waaaaay to the right I want the clock.

I wish I could just take screenshots, but I guess this will have to do since Xubuntu doesn't let you use printscreen. Any idea on how to stretch out the panel and rearrange the positioning of all these? Thanks in advance!

---

### Post by demosthenese on 2009-02-04
I'm not sure about your panel problem but for screen shots: Alt-f2 and enter

xfce4-screenshooter

and click Run.

---

### Post by Culgan on 2009-02-04
Thank you for the replies, folks. I can't run the screenshot program, guess I don't have it installed. I tried to sudo-apt get install it, but it cannot be found. No worries though, now that I've solved my Panel issues, I won't really need to take any screen shots for awhile. But perhaps it's in some other repository I can add to my sources list? 

Shipshape, I will indeed check out that page for further info, but luckily I figured out how to fix it on my own. For "Those Who Know" not how to fix the problem I described above, here's what I did:

I right clicked on my panel, went to customize panel, then made it Fixed Position instead of freely movable. Then I changed "normal width" to "Full Width" After that, it was just a matter of right clicking below items I wanted moved, then going to Move and just dragging everything into place.

---

