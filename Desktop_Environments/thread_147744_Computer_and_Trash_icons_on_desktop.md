---
title: "Computer and Trash icons on desktop"
date: 2006-03-20
forum: Desktop Environments
---

### Post by Sundel0802 on 2006-03-20
I just had Computer and Trash icons show up on my desktop after running the update manager. I don't know which of the apps put them there or why, but I can't figure out how to get rid of them. I liked the clean desktop look. How do I get rid of these?

---

### Post by dragomirov on 2006-03-20
open a console, run "gconf-editor", then in the "nautilus" section, then edit the desktop options

h&k

---

### Post by manicka on 2006-03-20
Applications-->System Tools--->Configuration Editor

apps-->nautilus-->desktop

---

### Post by Sutekh on 2006-03-20
Open the Configuration Editor from the Applications -> System Tools Menu

Look for the apps -> nautilus -> desktop enu on the left.  Then uncheck the boxes for the computer, trash, home, etc.

---

### Post by Sundel0802 on 2006-03-20
There is no section for desktop options. Under nautilus there is only preferences (as shown) and icon_view (which contains no entries).

---

### Post by Sundel0802 on 2006-03-20
Weird... It all fixed itself after a reboot. The desktop configs are back and the icons are gone.

---

