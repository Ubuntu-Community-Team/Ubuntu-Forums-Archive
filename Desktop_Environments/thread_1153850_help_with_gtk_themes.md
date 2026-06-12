---
title: "help with gtk themes"
date: 2009-05-09
forum: Desktop Environments
---

### Post by Dawei87 on 2009-05-09
ok. so i changed the colors on my theme to suit my needs, and now i have a slight problem on the corners that only affects the terminal. i have included a screenshot to show what i mean. its like small pieces of the corner are transparent, and it was not like that before. if anyone has any advice on how to fix it it would be much appreciated!

EDIT: one more thing i forgot, if anyone can help make the very corners of the metacity theme transparent that would be great!

EDIT: OK. somehow i just fixed the terminal problem. im still trying to find a way to make my corners nice and rounded though. any suggestions would be nice

---

### Post by gettinoriginal on 2009-05-10
System, Preferences > Appearance > Customize >  Window border tab.  Hope that is what you are looking for.  :P

---

### Post by Dawei87 on 2009-05-10
well, all that lets you do is select a metacity theme. i already have one, i just need to figure out how to make the corners transparent and round. im assuming i either need to activate a rgba setting somewhere or go back to gimp with the metacity images

---

### Post by Dawei87 on 2009-05-11
ok. i had to disect multiple metacity themes to figure it out. all i had to do was add "rounded_top_left="true" rounded_top_right="true" rounded_bottom_left="true" rounded_bottom_right="true"" to metacity-theme-1.xml. just in case anyone else wants to know...

---

