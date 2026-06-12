---
title: "desktop panel error"
date: 2008-03-12
forum: Desktop Environments
---

### Post by kadixt on 2008-03-12
hi everyone,
ive just installed ubuntu onto my computer and it seemed to be working fine. i installed the advanced effects stuff for the desktop so i could have those bendy windows etc. it worked fine for a while but now wen i open ubuntu ther is no panel or icons on my desktop. sometimes ther is a white box in the top left corner which flashes saying something like "panel encountered a problem with gnome_panel_transcript" - though im not sure about the exact wording because i cant read it wen it flashes really quick.
this is my first time installing linux so any help would be really appreciated.

thanks,
nelson

note  the desktop cube rotation still works, i just see 4 blank desktops though!

---

### Post by itix on 2008-03-12
What is working and what is not. This seams far more serious that desktop panels missing.

I need more information if I shall be of any help.

---

### Post by kadixt on 2008-03-12
i mean the top panel doesnt load and neither do the icons on the desktop. the mouse is still ther and so is the default desktop background (that orangey bird thing). i can still press ctrl-alt-right and flip round the 4 desktops i have. iv tried to use the failsafe gnome desktop but that doesnt work. the only error i get is the one "panel encountered a problem with gnome_panel_transcript"

my machine has a nvidia 7900gs graphics card btw

---

### Post by ajgreeny on 2008-03-12
To get out of compiz use Alt+F2 and in there type gnome-terminal.  A terminal should open and there you can use ```
metacity --replace
``` to go back to a standard desktop without compiz.  You could also try opening the "appearance" utility window with "gnome-appearance-properties" in the run dialogue.  From there you can try different compiz combinations using ccsm until you get something that works OK.

---

### Post by itix on 2008-03-12
I'll leave this one to someone who knows theese things better than me, but if more things than the panel is failing it's something to serious and deep down than I can handle. Sorry I couldn't be of any help.

---

