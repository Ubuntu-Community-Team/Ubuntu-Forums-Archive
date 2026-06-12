---
title: "no root access for 'run' command"
date: 2005-04-30
forum: Desktop Environments
---

### Post by neighborlee on 2005-04-30
unlike kde is there a reason there is no option> menu in 'run' dialogue to allow use of root ?

sometimes it would be nice not having to drop-to-shell just to run instance of gedit so I can alter certain files..

cheers
neighborlee

---

### Post by Professor X on 2005-04-30
You might be interested in [this project](http://xsu.sourceforge.net/).  Too bad it's not integrated into gnome's run dialog yet.

---

### Post by sethmahoney on 2005-04-30
[QUOTE=neighborlee]unlike kde is there a reason there is no option> menu in 'run' dialogue to allow use of root ?

sometimes it would be nice not having to drop-to-shell just to run instance of gedit so I can alter certain files..

cheers
neighborlee[/QUOTE]
 You can do this without calling up a terminal (I think).  In the run box type

gksudo *command*

---

### Post by atf487 on 2005-04-30
i would just run gksudo "app name"

and it would usually work, and be 'safer'.

edit: beaten to the punch.

---

### Post by neighborlee on 2005-04-30
[QUOTE=sethmahoney]You can do this without calling up a terminal (I think).  In the run box type

gksudo *command*[/QUOTE]
-----------
ah much better..thx good one to remember ;-00

I understand now why they dont do it in gnome directly  ( how does kde achieve this and maintain portability ?? ) albeit I wonder what platform doesn't support 'su' that gnome needs to support ?

thx
neighborlee

---

