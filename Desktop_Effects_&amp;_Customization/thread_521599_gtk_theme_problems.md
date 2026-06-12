---
title: "gtk theme problems"
date: 2007-08-09
forum: Desktop Effects &amp; Customization
---

### Post by Niklas Schröder on 2007-08-09
i'm working on making my own gtk theme and it's going great (slow, but great.  ;) ).  the only problems i've encountered is a few text colors.  

the first is on the tooltips.  i set the tooltip color to a blackish tint, but i can't figure out how to change the text to white.

the second is on firefox.  since firefox doesn't use GTK, the text on the almost-white drop-downs is white like on the rest of the menus.  

is there any way to fix these problems?

p.s.  it's a pretty dark theme, that's why i need the white text.

thanks!

---

### Post by ayoli on 2007-08-09
for the tooltips text try one of these:
```
  fg[PRELIGHT] = "#ffffff"
  text[PRELIGHT] = "#ffffff"
  fg[NORMAL] = "#ffffff"
  text[NORMAL] = "#ffffff"
```
for firefox drop down lists, you may have a look to /usr/lib/firefox/res/forms.css 
hope that helps

---

### Post by Niklas Schröder on 2007-08-09
ok.  i'll try that.  thanks!  :)

---

