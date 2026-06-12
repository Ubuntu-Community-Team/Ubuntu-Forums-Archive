---
title: "Compiz setting to show window on all desktops?"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by zach382 on 2008-04-15
Is there a compiz setting in one of the plugins that allows you to always display a certain window class/title on all workspaces?

---

### Post by Zorael on 2008-04-16
Certainly!

The plugin you want to activate is Window Rules. Then add the needed class/title identifiers [as detailed on this wiki page.](http://wiki.compiz-fusion.org/WindowMatching)

To figure out the class and title of a window (though you seem to know how to), is by running **xwininfo** in a terminal, and then clicking on the window you want to poll. Text will spam with some information about it, including title and class. Likely there are other ways of doing it, as well.

I set mine up to always show Konsole, Skype and Pidgin on all desktops. I'm on a l0sedows machine right now so I can't check the precise settings I used.

---

### Post by zach382 on 2008-04-16
Thank you! It worked beautifully! And thanks for the tip about xwininfo, I had no idea that existed. I was using the grab option  in compiz, but this gives me so much more information.

---

