---
title: "compiz needs to be manually started each session..."
date: 2009-12-01
forum: Desktop Environments
---

### Post by alex69 on 2009-12-01
Hi,

I'm a Karmic user, using a Nvidia Geforce 9500GT video Card.

I'm telling you about my GPU, because since I upgraded to the 190.42 Nvidia "official" new drivers, what's happening is:

My Compiz is no more able to save it's configuration across the sessions, and every time I close my PC or when I simply need to restart my active session, Compiz needs to be started again manually, It do not auto-activate by the compiz setting preferences.
Doing: System --> Preferences --> gnome-appearance-properties (TAB: "Visual effects") and click on "normal" checkbox, to activate the compiz visual effects.

Is there anyone able to teach me how to save the compiz activation, in order to avoid the manual, boring, repetitive, activation each time?

thank you in advance.

Alex

---

### Post by gradinaruvasile on 2009-12-01
Well compiz is tricky sometimes. I use 3 computers with nvidia cards and i had the same issue as you. I really dont know why is happening. Whatever, live with it, i usually suspend/hibernate my computers so i dont have to mess with this. 

Just use fusion-icon. Thats a big help here.

First open add/remove applications and set Show to [COLOR="Red"]All available applications[/COLOR].

1. Install it (search "fusion icon")from the add/remove apps. I would recommend installing CCSM along with it (search "ccsm" in add/remove apps).
2. Open System -> Preferences -> Startup applications, add a new launcher, the command will be fusion-icon - this way you will launch compiz or whatever settings are specified from the fusion-icon gui. You can specify "fusion-icon --no-start" if you dont want to launch compiz along with it (good if you have some problem with compiz).
 You will have a tray icon that is extremely helpful with compiz options - you can reload the window manager (compiz or metacity) if compiz crashes and you dont have window borders, set options (for nvidia cards the "loose binding" option speeds up 
compiz) and launch the compiz settings manager (CCSM) for customizing compiz effects such as enabling the cube, fishes etc.

---

### Post by alex69 on 2009-12-01
Thank you very much for your suggestion, now I'm realizing a new compiz experience.

thanks a lot

---

