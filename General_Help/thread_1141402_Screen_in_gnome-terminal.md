---
title: "Screen in gnome-terminal"
date: 2009-04-28
forum: General Help
---

### Post by tanha on 2009-04-28
I'm trying to have screen launch by default in gnome-terminal. It works fine under any of the tty's when I log in. But it only launches when I log in... so, I added "screen" to my .bashrc file to launch it automatically, but it spawns a bunch of sub-shells when opened this way. Does anyone know how to launch screen automatically in gnome-terminal without all the sub-shells being launched?

---

### Post by benj1 on 2009-04-28
i think i once did some sort of hack, to see if there was a PTS line with the 'who' command then if not start screen, does that make sense?.

---

### Post by tanha on 2009-04-28
> **benj1 said:**
> i think i once did some sort of hack, to see if there was a PTS line with the 'who' command then if not start screen, does that make sense?.

well, if I understand your statement, you sound like you wrote a sort of "if ; then, fi" script, but I don't see how I would implement this in this scenario...maybe you could elaborate a little, please?

---

### Post by phinullfermata on 2009-04-28
Go into "Edit Profile" in the menu.  In the Title and Command tab enter the command 'screen' into "Custom Command"  That should open a fresh screen session by default - if you want to re-attach to a certain session every time, just modify the command to do so.

---

### Post by tanha on 2009-04-28
> **phinullfermata said:**
> Go into "Edit Profile" in the menu.  In the Title and Command tab enter the command 'screen' into "Custom Command"  That should open a fresh screen session by default - if you want to re-attach to a certain session every time, just modify the command to do so.

:) Brilliant simply. Thanks!

---

