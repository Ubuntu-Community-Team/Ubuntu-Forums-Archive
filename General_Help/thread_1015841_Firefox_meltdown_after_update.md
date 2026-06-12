---
title: "Firefox meltdown after update?"
date: 2008-12-19
forum: General Help
---

### Post by fINTiP on 2008-12-19
My firefox sessions must have crashed last night while I was asleep, because I left it open last night and left my computer running.... an update had been pending, and so when I opened it this morning, it checked my addons for compatibility with the new downloaded version, and then opened a firefox sessions that had lost all of my tabs and all of my customizations to the program. I tried to open the "addons" menu, and it crashed. I opened it again, exact same procedure. I try to look at bookmarks, and there are none. I open the bookmarks page, and it crashes.

What the heck happened?

Update manager was running as I opened it, if that could affect it. Also, though I doubt it would have an effect, it seems my roommate closed my laptop lid at night. This does not cause sleep or hibernate, but does cause a glitch where my laptop screen will not come on when I open the lid. I have to type in my password blind, and then use my hotkey to open a terminal window, and then type in "sudo xset dpms force on", and I get my screen back. Everything is running as if nothing is wrong, and I've been using this workaround for some time... again, I don't think that affected firefox, but I'm really puzzled and really bothered.

If anyone knows of a better place to post this, I'd be much obliged; I tried to ask on the firefox developer's IRC, and have gotten no response there.

K

---

### Post by fINTiP on 2008-12-19
Also--

The second time I opened it, it checked for "compatibility of addons" with the new version *several* times. It did this again the third time. Then it opens the "your last session crashed. Restore?" window.

K

---

### Post by fINTiP on 2008-12-19
Last thing:

I just opened the "error console", which I've never used before. It has a TON of error notifications.

And

I opened it in terminal so I could see errors when it crashed.... but all I got was a segmentation fault.

Any idea what to do with this data?

K

---

### Post by FuturePilot on 2008-12-19
It could be that your profile got corrupted. Try renaming your ~/.mozilla directory so that Firefox will create a new one. It's a hidden directory so if you open your Home folder and press Ctrl+H you'll see your hidden files. Make sure to close Firefox before renaming it. If it doesn't work, you can just delete the newly created ~/.mozilla and rename the original one back to ~/.mozilla

---

