---
title: "&quot;Add New Panel&quot; selection disapeared?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by Mister LinOx on 2009-04-24
Well, I was messing around with my panels, and I accidentally deleted the bottom one while configuring. So when I go to the top and right-click, it comes to my surprise that the "Add New Panel" and "Delete Panel"(not even a faded button) are bot gone. The two separators that contained them are still there, though. Any idea on how to get it back?

---

### Post by fdrake on 2009-04-24
terminal:

ps -e|less
(look for "gnome-panel", and copy the 4 digit number on its line and press "Q" to exit)
kill the_4_digit_number
gnome-panel

this will restart your panel process. see if it works and let us know.

---

### Post by Mister LinOx on 2009-04-24
> **fdrake said:**
> terminal:

ps -e|less
(look for "gnome-panel", and copy the 4 digit number on its line and press "Q" to exit)
kill the_4_digit_number
gnome-panel

this will restart your panel process. see if it works and let us know.

Woo! Don't you just love how Linux is a community instead of a busy corporation?
Anyway, it worked, and I thank you.

---

