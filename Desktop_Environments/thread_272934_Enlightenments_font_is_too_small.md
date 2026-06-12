---
title: "Enlightenments font is too small"
date: 2006-10-07
forum: Desktop Environments
---

### Post by KhaaL on 2006-10-07
Hey all

My problem is that almost all themes in enlightenment use a very small font and it frankly hurts my eyes when I try to read it and it's the same thing with epplets (and epplets can't be resized either).

Is it possible to change the font size in the themes? if yes, how do I do that?

---

### Post by KhaaL on 2006-10-08
Another guy had found a way of dealing with this:

> 

after spending the best part of an afternoon, I have finally found out how to change the menu fonts:-
You need to edit the theme configs - for menus, you have to edit ~/.enlightenment/themes/your_theme_here/menustyles/menustyles.cfg

__TCLASS __BGN
__NAME "MENU"
__JUSTIFICATION 0

__NORMAL "slkscr/16"
__DRAWING_EFFECT __EFFECT_NONE
__FORGROUND_COLOR 120 120 120

__HILITED "slkscr/16"
__DRAWING_EFFECT __EFFECT_NONE
__FORGROUND_COLOR 255 255 255

__CLICKED "slkscr/16"
__DRAWING_EFFECT __EFFECT_NONE
__FORGROUND_COLOR 255 0 0

where "slkscr" is the font name (e.g. arial, tahoma, whatever) and the number after is the font size.

For the default font's, I've found they are usually in /usr/share/enlightenment/themes/theme_name/

for the dialog boxes, they are in the /dialogs/dialog.cfg in themes - same deal as above
THere will be some others...just haven't found them as of yet.

Last step is to purge the caches...not too sure so I just purged all of 'em 




Tip: If you want to find all the fonts used in your theme, look at the names of the font files (*.ttf) in the /ttfonts folder, and do a search and look for the fonts names in the config files in the theme folder. 

I still haven't figured out a way for epplets, if anyone can contribute with their knowledge, go ahead :)

---

### Post by NewbieSLP on 2008-04-23
Hi KhaaL! Thank you very much for posting the solution, my eyes are now a little bit less stressed!

NewbieSLP
MÉXICO

---

