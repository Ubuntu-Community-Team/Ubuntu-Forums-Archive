---
title: "Start gnome-panel with panel hidden"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-23
I have several panels on my desktop, and most of them I like to be hidden until clicked - but I am unsure how to make them start from a hidden state when i start up a new gnome session.  How do I go about doing this, or is it done by default somehow?

---

### Post by Jucato on 2006-06-23
I'm not entirely sure about the exact procedures for this (I'm posting from Kubuntu), but if you right-click on the Panel and select Panel Properties, there's an option there that makes the panel hide. The panel will pop-up/slide up when your mouse hovers over the side of the screen where the panel is hidden. (This is different from the hide buttons that you have to click).

---

### Post by Lunar_Lamp on 2006-06-23
Yeah, I know about that one.

It's what I am using as my current solution, but:
 - 1 - it doesn't slide in from the left/right (only from the bottom/top)
 - 2 - there is a longer delay when trying to activate it (i.e. unhide it) - the mouse needs to hover there for about a second or so before it pops up.

---

### Post by Jucato on 2006-06-23
Yeah, those are the same drawbacks that I experience, although I prefer the panel to slide up/down rather than left/right.

Is there an option in GNOME to manually save a session? so that you could save a session where you have hidden the panels (using the hide buttons) then choose to log in using that saved session. I'm not entirely familiar with GNOME (yet) so I can't be very helpful... :(

---

### Post by Supersaiyan.IV on 2006-12-14
This may not be the answer, but partial maybe..
This cmd will make gdesklet tray icon disappear on next boot:
> 
% sudo gdesklets --no-tray-icon


As to minimizing i think its impossible, unless you minimize them all using "Show Desktop" in the bottom left corner. When you press 'show desktop' again they will reappear.

Hope you'll find out the rest ;]
peace

---

### Post by mcduck on 2006-12-14
> **Lunar_Lamp said:**
> 
 - 2 - there is a longer delay when trying to activate it (i.e. unhide it) - the mouse needs to hover there for about a second or so before it pops up.
you can adjust the hide/unhide delays with Configuration Editor. Press alt-F2 and run gconfig-editor, then browse to apps/panel/toplevels/(your-panel-here) and change unhide_delay and hide_delay to your liking. The values are in 1/1000 seconds. I like 50ms for unhide and 700ms for hide.

---

