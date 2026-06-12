---
title: "gnome panel transparency (applets)"
date: 2005-04-09
forum: Desktop Environments
---

### Post by carlc on 2005-04-09
Please flog me if this question has been answered (not asked) before because I did search. I recently insalled Hoary and I am trying to make my gnome panel transparent. The panel itself is easy enough, but how can I make the applets and items on the panel all transparent?

---

### Post by humanity_to_others on 2005-04-09
[http://ubuntuforums.org/showthread.php?t=20769](http://ubuntuforums.org/showthread.php?t=20769) 
Use transset.

---

### Post by carlc on 2005-04-09
Thanks for the reply, I followed the instructions and then typed "transset .3" which gave me the crosshairs on the mouse pointer. I clicked the object that I wanted to make transparent (gnome main menu) and nothing happened but this was displayed in the terminal:

got arg .3
d is 0.3
opacity 0x7ae147a
Set Property to 0.3

I guess I need to read more before pointing and clicking because I have the feeling that I might majorly screw things up using this before knowing what the heck I am doing.

---

### Post by rosslaird on 2005-04-09
AFAIK, transparency in the panel for specific apps is set within those apps themselves (in other words, they have to be able to know when the panel is being set, and by how much, and to follow that setting).

transset also works, but man is it buggy.

---

### Post by carlc on 2005-04-10
I thought that most applets in hoary should have this ability. The only panel items that I have had any luck in making transparent are the program launch icons. The gnome main menu and gnome main menu bar as well as the sound and date all keep the system color.  ](*,)

---

### Post by c_dog on 2005-04-10
Right-click on the panel bar. Got to >properties>background. Click 'Solid Color' and set 'Transparent - Opaque' slider. to your desired level.
Having all the applets work with transparency doesn't work in all themes. The default 'Human' theme and 'Clearlooks' work just fine.

---

### Post by carlc on 2005-04-10
hey thanks, you pointed about something that i having not understood in that transparency is theme dependent, i guess my current one is not, so i will have to check out some others, thanks again!

---

### Post by carlc on 2005-04-10
ok, i am trying out the clearlooks theme but the notification area and window list still keep the system color. Is that normal?

---

### Post by Leif on 2005-04-10
I use the human theme, but transparency doesn't work for the notification area. everything else is fine.

---

### Post by hizaguchi on 2006-03-01
I can't figure out how to get the window list or notification area transparent either, but if you can deal with using keyboard shortcuts to switch windows you can just get rid of the window list, and the notification area fits nicely into a drawer, which works great for me since I just need it as a place for Gaim to live.

---

### Post by Tamacracker on 2007-06-20
I was told you have to hack the menu (programming) in order to modify the colors of the menus.

---

