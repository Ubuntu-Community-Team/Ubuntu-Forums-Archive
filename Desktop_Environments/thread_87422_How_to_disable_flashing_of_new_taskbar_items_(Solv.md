---
title: "How to disable flashing of new taskbar items? (Solved)"
date: 2005-11-08
forum: Desktop Environments
---

### Post by sandisn on 2005-11-08
Hello!

Don't know if i'm the only one, but i hate this "feature". For example, when i open some images with gimp I have to click on every flashing item in the taskbar just to make them stop. Maybe it is usable for people who use IM all the time, but for me it is really distracting. Is there a way to turn it off?

Thanks,
Sandis.

---

### Post by gabhla on 2005-11-08
Amen.  It's annoying.

---

### Post by melalcoolique on 2005-11-12
Try this:

Open Gconf (Configuration Editor) in your System Tools menu and locate /apps/panel/global/

Uncheck Disable_animations

---

### Post by bvc on 2005-11-12
Thx! I've been meaning to look into this, because it is annoying! Well, it was :p

---

### Post by sandisn on 2005-11-15
[QUOTE=melalcoolique]Try this:

Open Gconf (Configuration Editor) in your System Tools menu and locate /apps/panel/global/

Uncheck Disable_animations[/QUOTE]

Thank you! No more flashing on my desktop.

---

### Post by magnusbb on 2005-11-15
It's great that flashing of taskbar items finally arrived in GNOME; but it's not working as it should. For example, when chatting in GAIM, the windows flash when you get a new message. But the flashing items doesn't turn normal when you raise the window, you actually have to type something into that window, to get it back to normal.

And some windows just flash for nothing; I've eperienced it with non-GTK2 apps like XMMS.

---

### Post by sandisn on 2005-11-15
[QUOTE=magnusbb]It's great that flashing of taskbar items finally arrived in GNOME; but it's not working as it should. For example, when chatting in GAIM, the windows flash when you get a new message. But the flashing items doesn't turn normal when you raise the window, you actually have to type something into that window, to get it back to normal.

And some windows just flash for nothing; I've eperienced it with non-GTK2 apps like XMMS.[/QUOTE]

Quite right! I disabled flashing via gconf, but some windows just ignore that. And yes, I did killall gnome-panel. I don't know about xmms (since i doesn't use/have it), but gnome app install is flashing like insane. Hmmm, is this "feature" overdone?!

---

### Post by varunus on 2005-11-17
Magnus,

The way programs flash the taskbar is up to the program  The fact that you need to type is a GAIM setting.  You can change it to your liking.

Open up the preferences in GAIM, and go to "Message Notification" on the left side; there are options to change when the flashing goes away, including when typing into window (default), when window gains focus (what you want, i think), and "don't flash" (disable the WINDOW MANAGER URGENT option).

---

### Post by bvc on 2005-11-18
I found that this doesn't work at all for me. Maybe that's because that configuration has been there a long time and is for the animation of a hidden panel, not the flashing.....unless they tied it to the hidden panel config.

---

### Post by jinnk on 2006-07-07
Using Dapper and this fix didn't work.  First, I didn't find /apps/panel/global/disable_animations - but i have /apps/panel/global/enable_animations - which was already off anyway.  Tried toggling it anyway - didn't help.

So then I created /apps/panel/global/disable_animations as boolean and tried both true & false.  Still no luck.

Also tried killall gnome-panel between changes.  Apps still flash - including gconf-editor.

On the plus side - I've found that clicking on apps only stops it flashing until i click on another app.  But if I use Alt-Tab to switch apps it stops the flashing for a reasonable time.

Other than just simply annoying, I find that if I have lot's of apps flashing it really drags down the performance of my system.  I only have a simple ATI graphics card in a work laptop, which I expect many people have.

---

### Post by dunnerz on 2006-07-08
I tried the GCONF trick above, but it didn't help - The app in question is Crossover running lotus notes (my ubuntu system at work - I hate lotus notes, but thats something else completly different!) - anyway - I usually give lotus a whole "desktop/workspace" to itself and go off working in other workspaces, however, whenever i get a new mail, lotus appears flashing in the current workspace - very annoying (there are not options to turn this off in lotus).

It is very disrupting when trying to work - so if anyone has any ideas.......
](*,) 

thanks

---

### Post by strabes on 2008-04-02
Sorry to resurrect an old thread but is there still a way to disable this? Running hardy beta and it's extremely annoying when windows appear on other workspaces and are still flashing on my panel.

---

