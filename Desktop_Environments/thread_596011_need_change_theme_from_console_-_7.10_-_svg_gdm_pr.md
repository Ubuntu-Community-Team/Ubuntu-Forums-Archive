---
title: "need change theme from console - 7.10 - svg gdm problem"
date: 2007-10-29
forum: Desktop Environments
---

### Post by totmaga on 2007-10-29
Hello!

The original problem is:
Ubuntu doesn't show me the login(splash?) screen. It shows instead:
[I]
"There was an error loading the theme Human
Couldn't recognize the image file format for file '/usr/share/gdm/themes/Human/bottom_bar.svg"[/I]

I tried to "install" the debian svglib1 package, also tried to compile it from source, but it didn't solved.

So I think if I could change the theme to one that hasn't got .svg -s I could at least use my system.

I changed in my /usr/share/gdm.conf 
[gui]
GraphicalTheme=Human    ->   HumanCircle ,tried Edgy also (in the themes it hasn't got svg)
[greeting]
GraphicalTheme=Human -> HumanCircle

After I changed these I get a waiting cursor(and not the popup erroe) and nothing happens.


So if sy. could tell what I have to change or someone could paste a gdm.conf or whatever .conf I have to change, that I hope would be a big help!

Also tried recovery mode - when I startx I get some daemon error 127 and I couldn't change theme either from there.

Thanks - Matthew

---

