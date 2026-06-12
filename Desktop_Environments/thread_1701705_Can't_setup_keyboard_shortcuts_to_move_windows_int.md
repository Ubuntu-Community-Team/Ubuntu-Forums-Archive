---
title: "Can't setup keyboard shortcuts to move windows into other workspaces"
date: 2011-03-06
forum: Desktop Environments
---

### Post by jonbwilson on 2011-03-06
Using Ubuntu 10.10.  I'm trying to setup keyboard shortcuts to move windows into other workspaces so I don't have to right-click the title bar and select the workspace manually with my mouse.

I went into Keyboard Shortcuts under preferences and tried several different key combinations, but none of them worked.  Ideally, I'd like to use Ctrl+1, Ctrl+2, etc. for the 4 different workspaces. I also tried it with Alt, Ctrl+Shift, Alt+Shift, but none of those worked either. I can't find any conflicts anywhere, so I'm stumped as to why this isn't working.  Anyone else have this problem, or know of a different way to go about it?

---

### Post by Krytarik on 2011-03-06
It also doesn't work for me that way, because those keybindings are for Metacity, and I am using Compiz, I guess you too!?

To achieve what you want you have apparently to use the "Put" plugin of Compiz, you find it here: "System -> Preferences -> CompizConfig Settings Manager -> Window Management -> Put". That way worked for me.

Greetings.

---

### Post by ipatfrmww on 2011-03-06
This is odd, even if you have compiz shouldn't the keyboard shortcuts menu link to the compiz key bindings (so you don't need to install ccsm).
Somebody should post a bug about that.

---

### Post by Krytarik on 2011-03-06
> **ipatfrmww said:**
> 
Somebody should post a bug about that.
Sure, try it! ;-)
But it is more a missing feature than a bug, Compiz already has the "Gnome Compatibility" plugin, which supports the most common keyboard shortcuts, without those even Alt+F2 and Print wouldn't work.

---

### Post by jonbwilson on 2011-03-06
> **Krytarik said:**
> It also doesn't work for me that way, because those keybindings are for Metacity, and I am using Compiz, I guess you too!?

To achieve what you want you have apparently to use the "Put" plugin of Compiz, you find it here: "System -> Preferences -> CompizConfig Settings Manager -> Window Management -> Put". That way worked for me.

Greetings.

Bingo! Thank you!

---

### Post by ipatfrmww on 2011-03-06
I was thinking along the lines that if it isn't set-up in a logical way in a default install then it is a bug.
I think i will do that, when I have the time. Not right now though. Somebody might have already fixed it in natty.

---

