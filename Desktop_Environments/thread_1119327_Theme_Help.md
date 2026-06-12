---
title: "Theme Help?"
date: 2009-04-07
forum: Desktop Environments
---

### Post by higashi on 2009-04-07
Hello,

I used to use the Mac4Lin theme, and finally got tired of it. So i switched my theme and everything, but the close, minimize, and maximize buttons are still on the left side.

How can i get them back on the right?

EDIT: i am using the theme Inity. Another problem i'm encountering is that, whenever i open something new, it always appears at the absolute top of my screen.. so that the bar at the top is under my menubar. can i fix that too?

---

### Post by sekinto on 2009-04-08
[Alt+F2] gconf-editor [Enter]
Go to /apps/metacity/general
Change value of button_layout

Button layout examples:
menu:minimize,maximize,close (menu <--TITLE--> minimize maximize close)
close,maximize,minimize: (close maximize minimize <--TITLE-->)
close:minimize,maximize (close <--TITLE--> minimize maximize)

---

### Post by higashi on 2009-04-08
Thanks!

Now i just have the problems where the programs appear way too high up on the screen.

---

### Post by higashi on 2009-04-26
Bump

---

