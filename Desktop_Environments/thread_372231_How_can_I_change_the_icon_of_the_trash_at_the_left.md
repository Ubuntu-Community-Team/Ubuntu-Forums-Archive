---
title: "How can I change the icon of the trash at the left bottom?"
date: 2007-02-27
forum: Desktop Environments
---

### Post by chinese_ys on 2007-02-27
How can I change the icon of the trash at the right bottom on the bottom panel?
I use a MAC theme downloaded from gnome-look.
I changed something in the gconf-editor, but it did not work. I also changed back to ubuntu default theme with the changing in gconf-editor, it still does not work.

what configuration should i do?

thanks!

---

### Post by timjayko on 2007-02-27
hmmm only thing i can think of is switch around to other themes as well?

---

### Post by chinese_ys on 2007-02-27
> **timjayko said:**
> hmmm only thing i can think of is switch around to other themes as well?
I do not know what`s going on with other theme. but under the default, I can not change from gconf-editor

---

### Post by timjayko on 2007-02-27
sorry I am very new to ubuntu... best of luck

---

### Post by ComplexNumber on 2007-02-27
> **chinese_ys said:**
> How can I change the icon of the trash at the right bottom on the bottom panel?
I use a MAC theme downloaded from gnome-look.
I changed something in the gconf-editor, but it did not work. I also changed back to ubuntu default theme with the changing in gconf-editor, it still does not work.

what configuration should i do?

thanks!
the trash icon is dependent upon the theme. log out and then log back in again. it will change to the right theme when you log back in. 
for some reason, it doesn't seem to update with the theme at the time like most things do. i guess this must be something to do with gconf daemon. one thing that i noticed is that if i set my theme to Tango, THEN add the trash to my panel, it will be Tango themed. if i then change my theme to something like Human, it won't change. however, if i delete the trash icon from the panel, then add it again, it will by Human themed.

---

