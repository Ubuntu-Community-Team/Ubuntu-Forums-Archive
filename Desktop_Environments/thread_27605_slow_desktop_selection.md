---
title: "slow desktop selection"
date: 2005-04-16
forum: Desktop Environments
---

### Post by lee_connell on 2005-04-16
This has always been an issue for me, but does anyone notice that if you click and drag your selection/cursor from the bottom right of the screen to the top left of the screen too fast, that it's really slow to redraw it'self?  not a big deal but just annoying.

---

### Post by bored2k on 2005-04-16
I remember my 200mhz 60MB Ram doing the exact same thing on RedHat and my -attempt- at XP -there I couldn't even multitask with msn messenger-.

---

### Post by Stormy Eyes on 2005-04-16
[QUOTE=lee_connell]This has always been an issue for me, but does anyone notice that if you click and drag your selection/cursor from the bottom right of the screen to the top left of the screen too fast, that it's really slow to redraw it'self?  not a big deal but just annoying.[/QUOTE]

Use the gconf-editor, which is in **Applications -> System Tools -> Configuration Editor**, and turn on the "reduced_resources" option in /apps/metacity/general. Moving an opaque window tends to slow the system down, because X has to constantly redraw the screen. This is being worked on, particularly by the people working on the COMPOSITE and DAMAGE extensions.

---

