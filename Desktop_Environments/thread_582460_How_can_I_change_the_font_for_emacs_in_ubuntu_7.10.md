---
title: "How can I change the font for emacs in ubuntu 7.10"
date: 2007-10-19
forum: Desktop Environments
---

### Post by yinglcs2 on 2007-10-19
Hi,

I am trying to change the emacs font in ubuntu 7.10 like this:

$ echo "Emacs.font: Monospace-10" >> ~/.Xresources
$ xrdb -merge ~/.Xresources
$ emacs22-gtk
No fonts match `Monospace-10'

But I get a 'No fonts match'.

Can you please tell me how can i change the font of emacs in ubuntu 7.10?

Thank you.

---

### Post by szulat on 2007-10-20
from inside emacs: menu -> options -> customize emacs -> specific face -> "def" [enter] - this shows the default, you can change the font family, size, color, etc.

---

### Post by yinglcs2 on 2007-10-21
Thanks, I am trying to change the 'Font Family' of the default face.

So I go to Attributes: Font Family: and type 'monospace'

But it does not work. When I open the customization page again, I see 'adobe-courier' again.

Thank you for any more help.

---

### Post by szulat on 2007-10-22
it work for me, but i'm not using the "Monospace" font.
it seems that this font is simply not available as a regular x11 font (even though it is in the gnome/gtk font list), see xlsfont or xfontsel.
perhaps it has a different name in x11 or something else must be configured in ubuntu to make it available for all applications. unfortunately i don't know much about this subject.

(also make sure you are changing the "State" in emacs after configuring the font - "set for current session" or "save for future sessions")

---

### Post by softtower on 2008-02-11
Also you may check out this:
[http://kontsevoy.blogspot.com/2008/02/this-just-begs-to-be-shared.html](http://kontsevoy.blogspot.com/2008/02/this-just-begs-to-be-shared.html)

---

