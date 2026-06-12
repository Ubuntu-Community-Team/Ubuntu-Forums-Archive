---
title: "compose key combinations for uncommon diacritics"
date: 2009-05-28
forum: Desktop Environments
---

### Post by wmaheriv on 2009-05-28
Does anyone know if I can set key combinations (or if they exist) for less common letter/diacritic pairs, like &#7789; or &#7717; or &#7693;?  I use these frequently for transliterated Arabic, but I cannot find any information that would let me make them with the ease of normal diacritics (i.e., with the compose key).
Thanks.

---

### Post by Hendrik0 on 2009-06-11
Yes, you can do that with an .XCompose file. Copy your /usr/share/X11/locale/en_US.UTF-8/Compose (replace locale) to ~/.XCompose. Then you can add combinations. If you have a compose key configured (which you could do anyway), you might add e.g.

```
<Multi_key> <period> <d>		: "&#7693;" U1e0d
```

This probably works after relogging, so that you can hold Compose and type "." and "d" consecutively, you get "&#7693;". If it doesn’t work, maybe you have to switch to X Input Manager (xim) input method.

Better still, you can use an .Xmodmap file to set a belowdot deadkey. If you have no ~/.Xmodmap, go into your home directory and type

```
xmodmap -pke > .Xmodmap
```

Then edit the file and set e.g. any "alt gr" combination you do not need to "dead_belowdot". Then you can add to your .XCompose:

```
<dead_belowdot> <d>		: "&#7693;" U1e0d
```

and so on (you can use Gnome Character Map to find the unicode, it’s in "Latin Extended Additional"). You could also use .Xmodmap to set a compose key, keysym is "Multi_key". Have fun.

---

