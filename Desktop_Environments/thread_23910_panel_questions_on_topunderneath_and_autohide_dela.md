---
title: "panel questions: on top/underneath and autohide delay"
date: 2005-04-04
forum: Desktop Environments
---

### Post by 23meg on 2005-04-04
i have two questions regarding panels in Gnome; i searched both here and the gnomesupport.org forums but found nothing relevant.

1) do the panels have to be on top of everything else all the time? is there a way of making a particular panel "go underneath" windows when you maximize them or when they overlap with that panel? i'm sensitive about not wasting any screen space; i want applications to have the widest space possible, and keep a bottom panel to use as just for launchers at the same time.

2) there's a disturbing delay of about 500ms before a panel with the "autohide" option on reappears when hovered on. is there a way of totally removing this delay so that the panel appears (and also disappears) immediately?

---

### Post by Lustiger Lurch on 2005-04-04
the answers to your questions.....  would be very interesting for me, too :)

---

### Post by 23meg on 2005-04-04
found a solution for the second one:

in gconf-editor enter a value of 0 for the /apps/panel/toplevels/bottom_panel_screen0/hide_delay and /apps/panel/toplevels/bottom_panel_screen0/unhide_delay keys .

---

### Post by Lustiger Lurch on 2005-04-04
[QUOTE=23meg]found a solution for the second one:

in gconf-editor enter a value of 0 for the /apps/panel/toplevels/bottom_panel_screen0/hide_delay and /apps/panel/toplevels/bottom_panel_screen0/unhide_delay keys .[/QUOTE]

ahhh great

for me it was /apps/panel/toplevels/panel_0/

auto_hide_size = 0 tastes very nice.. so a hidden panel is now really hidden :)

---

### Post by 23meg on 2005-04-04
yes, i changed that too. now that the bottom panel is automatically hidden this kind of solves the first problem as well  :-D  but i'd still like to know if there's a way to tweak the panel behaviour so that it will go underneath a maximized window without being auto-hidden.

bonus: while i was messing with xcompgr (see [this thread](http://www.ubuntuforums.org/showthread.php?t=20769&highlight=windows+super+sweet)) i noticed it has a bug that makes windows totally ignore panels and go over them! this only happens if you run xcompmgr from the terminal, not at startup. one man's bug, another's solution...

---

### Post by trash on 2005-05-26
now thats cool!

thanks 23meg

---

