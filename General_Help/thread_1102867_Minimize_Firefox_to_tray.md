---
title: "Minimize Firefox to tray"
date: 2009-03-22
forum: General Help
---

### Post by larrel on 2009-03-22
I thought it'd be cool to have firefox appear/hide at the press of a hotkey(similar to Tilda :p)

So i embarked on a journey to find out whether its possible

I found a neat plugin called [COLOR="Blue"]Firetray[/COLOR], which minimized/revealed firefox at the click of the tray icon.....but i just couldn't find a way to bind some hotkey to a "click on that tray icon" :sad:

Was already planning to ask about that here, but i was (im)patient and searched for a different solution:

Found a nice program called [COLOR="Blue"]alltray[/COLOR], which did pretty much the same .. but with any program/window
And again, i couldn't find a way to bind it to a hotkey

Thats why i am asking here, anyone?

---

### Post by larrel on 2009-03-22
.

---

### Post by Ms_Angel_D on 2009-03-22
As far as I know there is no way to bind the function to a hot key. You could write the developers of firetray and alltray asking them to impliment such a function. Most OSS developers welcome feedback, input, and new ideas.

---

### Post by ashcroft3000 on 2009-07-19
I yet haven'd tried alltray 0.7 which seems to be completely rewritten and - from what I've got from the dev site - has a whole new behaviour. But with alltray 0.69 (that's the version in the repositories) you can easily bind hide/unhide to a hotkey, e.g. "alltray --key F9 firefox". You could also use xbindkeys and/or xdotool to bind this functions to additional keys (alltray 0.69 only allows "control", "alt", "altgr" and "shift" as modifiers - but they don't work reliable, at least on my machine).

Personally, though, I would prefer if my usual shortcut for closing a window (control + q) would hide firefox and another shortkey, say win+f, would bring it back. The first thing is what seems to hard achieve, though. Right now the only way I see to do this is through a firefox-addon grabbing/monitoring that key. But neither Firetray 0.1.x (the version on addons.mozilla.org) nor new FireTray 0.2.3 have any keybinding functionality...

---

