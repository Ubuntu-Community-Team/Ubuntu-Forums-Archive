---
title: "Remap single key (Caps Lock) as arbitrary keystroke?"
date: 2011-01-02
forum: Desktop Environments
---

### Post by Kalimol on 2011-01-02
Odd question - like many folks, I don't use Caps Lock, and right now, it's just a dead key. I know I can remap it to any *single* key by turning it back into Caps Lock in my keyboard layout, then creating a startup script to remap it, but it's made to not repeat (one signal per press) and not to combine with anything else in the hardware, so I can't use it as an extra Super or anything like that, and I don't really need one regardless. What I'm wondering is whether or not it would be possible to remap it to a common keystroke, like Alt+F4, Alt+Left, or Ctrl+I, that I use on a regular basis.

Weird question, I know. It's something I'd been thinking about before the Google CR-48 did it at the hardware level, and now I really want that. = )

Thanks!

---

### Post by manki on 2011-10-25
It looks like this is possible, but not directly.  Essentially, you'd:
[LIST]
[*]configure xmodmap to send a different key code when Caps Lock is pressed
[*]configure Gnome or KDE to run [FONT="Courier New"]xte[/FONT] with the keystrokes you want.
[/LIST]
I have posted this on my blog at [http://linuxtips.manki.in/2011/10/opening-new-browser-tab-when-caps-lock.html]("http://linuxtips.manki.in/2011/10/opening-new-browser-tab-when-caps-lock.html").  Hope this helps.

---

