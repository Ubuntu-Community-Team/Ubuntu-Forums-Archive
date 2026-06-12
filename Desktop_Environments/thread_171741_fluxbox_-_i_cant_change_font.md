---
title: "fluxbox - i cant change font"
date: 2006-05-07
forum: Desktop Environments
---

### Post by siarski on 2006-05-07
Hi,
Thats the problem:
I compiled and install fluxbox from the howto, I install some new theme, 
because I have some ugly font I go to the theme.cfg, and wrote f.e.: 
*.font: tahoma-20 
the font havent changed, also if I comment all fonts sections the font is the same. I also tried to changed the antialiasing section in .fluxbox/init, its always the same font for true and false.
the font only change if i put there f.e. -misc-*-*-*-*-*-*-200-*-*-*-*-*-* those are xfonts, very ugly, so how can i use the normal ttf-fonts, like this: *.font: tahoma-20,
I have done the ttf-how-to and i have tested many fonts and nothing solved my problem.

Anybody could help me? The only solution i thought about - was to remove fluxbox and install it from deb,
Cheers

ps. of course in other programs like oo, firefox i have working fonts.

---

### Post by Googler on 2006-05-21
[QUOTE=siarski]
*.font: tahoma-20 
[/QUOTE]

just remove the star and dot (*.) make the line begin with font

thats it , but size of 20 is too much let it 12 or 14

---

### Post by bugz0r on 2006-12-26
I notice that this does not change the font of everything. For example, the firefox and rox-filer still have the old font(the font does not change with theme).

---

