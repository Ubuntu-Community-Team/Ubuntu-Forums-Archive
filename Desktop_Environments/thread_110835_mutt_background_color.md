---
title: "mutt background color"
date: 2005-12-31
forum: Desktop Environments
---

### Post by rosslaird on 2005-12-31
I'd be very happy if I could get mutt to preserve the terminal color that I use (a dark-ish gray). But when I start mutt, it always uses a black background. I've read about a patch to fix this, but that's beyond me. Is there a simpler way to get this working properly? (I also have mutt-ng)

Ross

EDIT:

OK, got it from the web:

> 
If you also use a transparent terminal, put this in your .bashrc export COLORFGBG="default;default"

The first field is the command color. Second field is the object you want to alter in mutt. The third and fourth field specify the foreground and background color. If there is a fifth field, its the regular expression you want your colors to apply to. Change default to another color if you want another background color. Color values can be preceded by "bright" resulting in bold, bright text. Consult the mutt manual for more info.

color normal		default		default
color hdrdefault	brightcyan	default
color signature		green		default
color attachment	brightyellow	default
color indicator		brightblack	brightcyan
color quoted		green		default
color quoted1		white		default
color tilde		blue		default



---

