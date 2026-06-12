---
title: "UK Dvorak and Linux"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-22
OK... I need to write a keyboard map to tell the OS that my keyboard is not ANSI Dvorak, but UK Dvorak - that's unofficial, so you can't download them.

So is there a text file that says:

key_01 #
key_02 1

Or something?

Thanks

---

### Post by Alexander Kirillov on 2005-06-23
[QUOTE=Dave_is_sexy]OK... I need to write a keyboard map to tell the OS that my keyboard is not ANSI Dvorak, but UK Dvorak - that's unofficial, so you can't download them.

So is there a text file that says:

key_01 #
key_02 1

Or something?

Thanks[/QUOTE]
 Yes, there is. But the syntax is slightly more complicated. See this article:
[http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html)
By the way: if you want to search for other solutions (there may be a symbols file for UK dvorak - I do not know), you should know htat Ubuntu (and all more or less recent X servers) uses xkb mechanism, not older xmodmap. You do not need to understand what this means, just ignore everything which talks about xmodmap, and look for xkb.

---

