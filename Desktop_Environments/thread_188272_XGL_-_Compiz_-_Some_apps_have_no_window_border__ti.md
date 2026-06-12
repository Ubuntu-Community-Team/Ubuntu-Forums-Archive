---
title: "XGL - Compiz - Some apps have no window border / title"
date: 2006-06-03
forum: Desktop Environments
---

### Post by ariel on 2006-06-03
Hi!
Today I installed XGL/Compiz and in general i'm very well impressed but the new stuff. The only quirk i found (appart from the poor video playback performance) is that a few applications like:

    - amule
    - keepassX

don't  show a window border (and they have no title nor "window controls" - minimize, close, etc)

Any idea/hint on how this can be solved?

Thanks!

---

### Post by jaymode on 2006-06-03
[QUOTE=ariel]Hi!
Today I installed XGL/Compiz and in general i'm very well impressed but the new stuff. The only quirk i found (appart from the poor video playback performance) is that a few applications like:

    - amule
    - keepassX

don't  show a window border (and they have no title nor "window controls" - minimize, close, etc)

Any idea/hint on how this can be solved?

Thanks![/QUOTE]
I know this sounds silly but I had that issue once but I had to right click on the program on the bar at the bottom of the screen and tell it to maximize.

Not sure what version on XGL/Compiz you are running, but the latest versions available from [www.compiz.net](www.compiz.net) are much better. They can also help over there too.

---

### Post by ariel on 2006-06-03
Thanks for the quick reply.

Yes I just upgraded compiz & xgl using:

    deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
    deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

and this fixed all problems. This thing is such a nice piece of work.
Also found the fix for  "shift-backspace" killing X:

    xmodmap -e "keycode  22 = BackSpace" &

I installed this a few hours ago, but i don't think i'll ever have a desktop without this in the future :-)



[quote=jaymode]I know this sounds silly but I had that issue once but I had to right click on the program on the bar at the bottom of the screen and tell it to maximize.

Not sure what version on XGL/Compiz you are running, but the latest versions available from [www.compiz.net]("http://www.compiz.net") are much better. They can also help over there too.[/quote]

---

