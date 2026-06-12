---
title: "Resetting Panels to Default behavior"
date: 2009-08-25
forum: Desktop Environments
---

### Post by TBerk on 2009-08-25
My system froze one day last week (1st time I can remember) and upon reboot I found my top or the screen and bottom of the screen panels had been 'damaged', or altered.

I deleted the bottom one and added a new one but what I had was:

- Top panel had date/time, shut down, wicd, 'pulse-audio applet, and a few icons for applications I had drug up there- ones I use often.

- Bottom Panel had 'currently running apps/windows', trash can, and I don't remember too much being down there.

Now the running apps/open windows show up in the upper panel along with the time/date and so on.  I'd like the bottom panel to be where the currently open 'windows' reside.  how can I default them there?

Thx,
berk

PS- I running Ubuntu Studio over the top of 9.04

---

### Post by mcduck on 2009-08-25
What do you mean "damaged" or "altered"?

If your panel applets had moved around, you could just have moved them back to where you want them to be.

If you want Window List-applet to be in bottom panel, just put it there instead of putting it into the top panel. ;) Or move it into correct place (right-click->Move, or drag with middle mouse button. If it doesn't move, make sure it's not locked (right-click->Lock to Panel)

---

### Post by TBerk on 2009-08-26
Lets see if I can be more clear;


Before:

Up top I had date/time, audio applet, etc, etc. I had pull down menus that included the normal stuff like 'office', 'Sound & Video, 'Internet', etc.

Down below I had a strip that would hold the Trash, open applications (if minimized, you would click 'here' to open them back up large again.) 


NOW: 

Up top I have a combination 'what apps are running' and Start menu Panel combined into one.


berk

---

### Post by Andreas1 on 2009-08-26
you could reset the panel settings by typing into an terminal:

```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

---

### Post by mcduck on 2009-08-26
> **TBerk said:**
> Lets see if I can be more clear;


Before:

Up top I had date/time, audio applet, etc, etc. I had pull down menus that included the normal stuff like 'office', 'Sound & Video, 'Internet', etc.

Down below I had a strip that would hold the Trash, open applications (if minimized, you would click 'here' to open them back up large again.) 


NOW: 

Up top I have a combination 'what apps are running' and Start menu Panel combined into one.


berk
Yes, I understood that. But every single thing you see in your panel are just separate applets, and they can all be moved around freely and put into any panel you want.

There is no applet that would combine the "start menu" (Menu Bar-applet) and running apps (Window List-applet) into one thing, so you already have those two individual applets in your panel. All you have to do is to drag the Window List applet from the top panel into bottom panel. :)

---

### Post by TBerk on 2009-08-26
> **mcduck said:**
> Yes, I understood that. But every single thing you see in your panel are just separate applets, and they can all be moved around freely and put into any panel you want.
[//quote]

Well, I understood that. But thx.

[quote]
There is no applet that would combine the "start menu" (Menu Bar-applet) and running apps (Window List-applet) into one thing, so you already have those two individual applets in your panel. All you have to do is to drag the Window List applet from the top panel into bottom panel. :)

Well, what I ended up doing was to move the panel that was defaulting to hosting the 'running apps' to the bottom of the screen (just a personal preference...) and creating a new panel at the top of the screen and populating it by and to recreate what I used to have.

What I had been asking about was a sort of "where is the Reset Button" but all the code I got from helpful people didn't rest it back to what was set during the initial OS install.

I appreciate everyone's involvement.  Thx again.


berk

---

### Post by TBerk on 2009-08-26
> **Andreas1 said:**
> you could reset the panel settings by typing into an terminal:

```
gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

I am almost tempted to try this, and will keep it 'on file' so to speak (it looks very simular if not exactly something I tried already via another thread.)

Since I manually reconfigured the panels to my liking I'll leave well enough alone.

For now.

(You know how people are about leaving well enough alone...)


Thx,
berk

---

