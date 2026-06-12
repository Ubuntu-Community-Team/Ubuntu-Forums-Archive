---
title: "Screenlets widgets not in any cube desktop"
date: 2007-05-04
forum: Desktop Environments
---

### Post by bullgr on 2007-05-04
hi...

i installed beryl and screenlets and works ok by now...
the only problem is that i can't get the screenlets widgets in any desktop when i rotate the cube.
the screenlets widgets are only in one desktop (there i boot).
i don't know if the "sticky" option in the widgets does the job but i try to enable it and it does not.
i enable (checkbox) "sticky" and when i right click again to check it, it's disabled again.

can someone help me how i get the screenlets widgets in any desktop when i rotate the cube?
it's the "sticky" option i need to enable?
and if yes, how can i enable this option? maybe from the widgets text configs?

thank's...

---

### Post by bullgr on 2007-05-04
i found it...

to get the widgets in any cube desktop the option "sticky" must be enabled.
like i afraid, the options i give in a widget don't take it (don't ask why) in the text config file of each widget.
so, it must be done manualy...
go to /home/username/~.config/Screendesklets and open the text config file of each widget with an
text editor (gedit), change the sticky option from "False" to "True" and save it.

thank's...

---

