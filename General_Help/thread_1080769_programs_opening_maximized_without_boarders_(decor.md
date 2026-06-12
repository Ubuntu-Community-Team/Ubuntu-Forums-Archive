---
title: "programs opening maximized without boarders (decorations)"
date: 2009-02-25
forum: General Help
---

### Post by rmausser on 2009-02-25
Hi

I am using Ubuntu Studio 8.10 on an HP pavilion and an Nvidia graphics card.

I did a recent update, and restarted the computer.

Now, programs open in full screen without boarders (or decorations)

I am using Cairo-dock. When I right click on an icon of an app that is open and 'unmaximize' it, the decorations appear fine. 

It is only when a program is open, and programs want to open maximized without boarders...even programs that generally don't have a maximized setting get "stretched" to full. 

I have tried gtk/emerald and compiz/metacity, and with or without the restricted Nvidia driver.

Nothing has fixed this yet.

Any ideas?

Thanks

Rob

---

### Post by rmausser on 2009-02-26
I would like to mention that cairo-dock has nothing to do with this either. 

I got rid of it and am using the regular taskbar windows manager that comes with ubuntu now. 

This must be something to do with GTK. If say I open songbird or a non-GTK program it opens fine... but GTK apps seem to open full screen...without boarders (AKA decorations)

here is a lovely screenshot attached. See how Firefox is filling the entire screen, without any top border with a 'minimize', 'restore' and 'close' button. If I right click on the taskbar item for firefox and say "un-maximize" it will shrink to 'restore' size and the border reappears. 

This is happening with everything but I used firefox as an example.

Please, no one? really annoying this is. 

Thanks

Rob.

---

### Post by geirha on 2009-02-26
Very odd indeed. Have you tried creating a new user, logged in with that new user and seen if it exhibits the same behavior? If the new user works as normal, then there must be a user setting that's a bit off. If the new user exhibits the same behavior, then it must be more systemwide. 

Another thing to try, open an application from the terminal instead of the menus. Run ```
firefox
``` in the terminal for intance, then close it and look through the output firefox has generated in the terminal. Any clues?

---

### Post by rmausser on 2009-02-26
I have created a new user.

The same thing happens, which leads me to believe this is not something to do with my user account, but is system wide. 

This happened after I did a "partial system upgrade", as some package upgrades needed this to happen. Are partial upgrades bad? Should I not do them?

I opened firefox from terminal. Same fullscreen issue happened. I closed firefox and terminal gives me no messages. Actually the funny thing is that terminal opens full screen as well.

Any more suggestions? I'd love to search around for this, but it seems to be a very specific issue. 


Thanks

Rob.

---

### Post by Therion on 2009-02-26
You're running Compiz, correct?

Open CCSM (Compiz Config Settings Manager).
Scroll down to the Utilities section.
Open the "Workarounds" plugin.
UN-check the tic-box labeled **Legacy Fullscreen Support**.

See if that solves the problem.

---

### Post by rmausser on 2009-02-26
I am running compiz, but I disabled it and same issue with metacity. 

Also in compiz fullscreen support was unticked. 

Thanks, but not solved yet.

---

