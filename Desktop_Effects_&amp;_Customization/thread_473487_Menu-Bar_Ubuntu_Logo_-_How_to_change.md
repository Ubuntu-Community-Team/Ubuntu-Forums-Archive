---
title: "Menu-Bar Ubuntu Logo - How to change ???"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by kevanf on 2007-06-14
Hi Everyone.

I am trying to replace the Ubuntu Logo that is next to the applications menu in the Menu Bar

This question has been posted before, however I have followed all suggestions that have been posted and am stuck.

I have replaced ALL icons and there is not a Ubuntu icon to be found, but when the computer re-starts it is still there.

I have deleted the Menu panel - created a new one etc. etc but it just will not go away.

Can anyone Help. 


Thanks

Kevanf

---

### Post by ferronica on 2007-06-14
To install:
Just move the start button icon somewhere and use it as the GNOME Main Menu button's icon. You can do this in the GNOME Configuration Editor, in about 30 seconds.

1) Start "gconf-editor" in the terminal.
2) Under apps > panels > objects > object_X, where X is the number of the "object" that is type "menu-object", check 'custom icon' on the right and give a path to the icon under 'custom_icon_path'


Move the panel somewhere and set it as the panel background by right clicking, selecting properties, and selecting the background tab. Change the panel size to 36px to use the the larger version. Use the 24px one if you want to leave your panel small.
:):):):):)

---

### Post by kevanf on 2007-06-14
Thanks Everything OK now.

---

### Post by mthakur2006 on 2007-06-14
i tried that but it stays the same :confused: :confused: :confused:

---

### Post by kevanf on 2007-06-14
I found that after I changed all the icons you need to load the Themes and then select the icon theme Tango or Tangerine this should fix all problems. I am working on a complete instruction set to do it all and will post when done.

---

### Post by deepclutch on 2007-06-22
do post a hw2

---

### Post by anubis3000bc on 2008-04-26
im changing the human theme and i got one icon to change which is (About ubuntu icon but start icon will still not change.So maybe i have to go back in because now im thinking that i forgot to change one.

---

