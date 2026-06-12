---
title: "Change dsesktop icon with bash script"
date: 2017-02-19
forum: Desktop Environments
---

### Post by anutosho on 2017-02-19
Hello guys,
I made a script to easily change the CPU governor from "powersave" to "performance" and vice versa and created starter for it on the desktop.
One start of the script switches to performance mode, the next one switches to powersave and so on.

To reflect the current function in the program icon, my script changes the "Icon=" entry in the .desktop file (with a sed script) depending on the current governor state. But this change does not show up on my desktop.
After I right click the starter icon -> properties -> OK the changed icon shows up correctly.
Obviously the preferences dialog fires some trigger that causes a redraw of the desktop icons.

Which function is this?

---

### Post by anutosho on 2017-02-19
Oops, just found it after an hour of fruitless searching:

Simply touch the desktop folder :)

---

