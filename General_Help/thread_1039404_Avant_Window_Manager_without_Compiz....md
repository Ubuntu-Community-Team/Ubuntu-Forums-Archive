---
title: "Avant Window Manager without Compiz..."
date: 2009-01-14
forum: General Help
---

### Post by icanfly0307 on 2009-01-14
Hi, is it possible to have Avant Window Manager working without Compiz? My graphics card isn't capable of utilizing Compiz, so I can it work without it? I really don't need the effects, so just as long as it AWM works normally, everything'll be alright. Thanks for your suggestions...

---

### Post by Sand &amp; Mercury on 2009-01-14
Avant Window Navigator requires a compositing window manager to function properly, but Compiz is not the only window manager to offer compositing. Metacity (GNOME's default window manager) also has compositing, you can enable it by hitting, alt-f2, typing in 'gconf-editor' and hitting Run.

Then navigate to apps -> metacity -> general and check 'compositing_manager'. Metacity's compositing is pretty fast, much faster than compiz in my experience. If it doesn't do it for you, you can get xcompmgr from synaptic which is also very fast, though a bit rough around the edges imo.

---

### Post by icanfly0307 on 2009-01-14
Alright!!! I never knew that metacity had a compositing manager... Good to know. I just hope that it won't slow down my system. Thanks...

---

### Post by timcredible on 2009-01-14
awn will run without compiz, and you don't need to enable compositing in metacity to run awn.  however, none of the 3d stuff will work.  awn looks bland without the 3d bar and no 3d effects, but it does run

---

### Post by brettybaby on 2009-12-18
is there a way to get this command to post so you do not have to keep posting it to start AWN?

as soon as I close the terminal AWN quites

AWN will only work with the terminal open after this command is executed

*xcompmgr && avant-window-navigator*

---

### Post by darco on 2009-12-18
Enter the command line in System/Preferences/Startup applications....



darco

---

