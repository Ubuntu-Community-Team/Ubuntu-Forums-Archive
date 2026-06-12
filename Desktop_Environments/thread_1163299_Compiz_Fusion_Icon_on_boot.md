---
title: "Compiz Fusion Icon on boot"
date: 2009-05-18
forum: Desktop Environments
---

### Post by PhilMize on 2009-05-18
I cannot enable desktop effect in jaunty on my laptop. O well... What I can do is use the compiz fusion icon as a workaround to get the enabled. BUT! Is there some sort of script I can run so that not only compiz fusion icon opens on boot but reloads the window manager? Let me clarify, I can get it to open on boot with startup applications, but is there a way to make it refresh my window manager automatically, instead of hafting to do it manually everytime.

;)

---

### Post by sherl0k on 2009-05-18
I'm going to guess that you have fusion-icon installed and running startup. It *should* automatically switch your desktop manager to compiz, provided that the last time you logged out/shut down safely you had Compiz running.

If that doesn't work, then add *compiz.real --replace* to your autostarted applications. That is a sure-fire way to get compiz running on login.

---

