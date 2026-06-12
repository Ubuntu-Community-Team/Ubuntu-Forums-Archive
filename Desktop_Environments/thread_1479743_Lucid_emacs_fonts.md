---
title: "Lucid emacs fonts?"
date: 2010-05-11
forum: Desktop Environments
---

### Post by spitzanator on 2010-05-11
Hey!  I just upgraded to Lucid, and the default emacs font, whatever it is, is beautiful.

How can I:
a) figure out what the font is that I'm looking at
b) find out where that font is being set (is it in .Xresources? my .emacs? some global, systemwide default for either of these?)

Thanks!

-Matt

---

### Post by jpkotta on 2010-05-11
> 
a) figure out what the font is that I'm looking at

M-x customize-face RET default RET

When I run emacs -q, it says it's using Deja Vu Sans Mono, which is a very nice font indeed.  I usually use Luxi Mono, though.

> 
b) find out where that font is being set (is it in .Xresources? my .emacs? some global, systemwide default for either of these?)


It could be set in any of these.  I don't know enough about the system files to say where it's most likely to be, but it doesn't really matter if you can customize things with your user config files.  Personally, I set emacs faces with the built in customize system, which will put the settings in your ~/.emacs by default.

---

