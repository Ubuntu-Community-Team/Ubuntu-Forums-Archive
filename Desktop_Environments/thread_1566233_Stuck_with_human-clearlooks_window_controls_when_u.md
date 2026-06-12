---
title: "Stuck with human-clearlooks window controls when using compiz effects"
date: 2010-09-02
forum: Desktop Environments
---

### Post by amorfis on 2010-09-02
Hello,

I cannot change my window controls to Ambiance theme when compiz effects are on. When I turn off compiz effects, theme selection works as a charm, but when I turn compiz effects on again, I get back to human-clearlooks. In *Appearance Preferences -> Theme* I can still see Ambiance is selected, but window controls are from human-clearlooks. Every theme changes only colors, icons, fonts etc, but window controls remain. And remain on the right side of window.

Everything works as expected when I turn off compiz effects.

In *CompizConfig Settings Manager -> Effects -> Window Decoration* Command is specified to [FONT="Courier New"]/usr/bin/compiz-decorator[/FONT]

What can I do to have buttons of the left side? I tried to change in [FONT="Courier New"]gconf-editor[/FONT] in *apps -> metacity -> general -> button_layout* to "close,minimize,maximize:menu", but it still has no effect on compiz

---

### Post by stinkeye on 2010-09-02
Try using 
```
gtk-window-decorator --replace
```
for the CompizConfig Settings Manager -> Effects -> Window Decoration Command

---

### Post by amorfis on 2010-09-03
This was not working.

The problem was in gconf. I had to run gconf-editor, go to apps -> gwt and check use-metacity-theme.

Now it works :)

---

