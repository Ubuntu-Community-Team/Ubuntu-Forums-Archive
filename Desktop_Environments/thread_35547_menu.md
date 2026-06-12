---
title: "menu"
date: 2005-05-19
forum: Desktop Environments
---

### Post by toran on 2005-05-19
Ok guys. I'm on ubuntu (obviously), running fluxbox.

In fluxbox, I have a custom menu, set up with all the applications I like, HOW I like it. Here's the problem: whenever I apt-get install stuff, my beautiful menu is **overwritten**. It's driving me insane. How do I stop it from getting overwritten with the default system crap-menu?

Thanks!

---

### Post by artio on 2005-05-20
I have my fluxbox custom menu in ~/.fluxbox/menu and the line 

session.menuFile:  ~/.fluxbox/menu

in ~/.fluxbox/init

It never gets overwritten, try it.

---

### Post by Psquared on 2005-05-28
[QUOTE=artio]I have my fluxbox custom menu in ~/.fluxbox/menu and the line 

session.menuFile:  ~/.fluxbox/menu

in ~/.fluxbox/init

It never gets overwritten, try it.[/QUOTE]


Pardon me for barging in on this thread, but it was the closest to a question I have about Fluxbox.

I cannot get my menu to work. Its in the right location, but when I right click on the desktop all I get is the Fluxbox default menu. I don't seem to be able to use fbdesk, fbpager, fbpanel or change themes.

---

### Post by Psquared on 2005-06-02
To followup, my menu was not in the right location. I changed it and all is well. I love the Fluxbox minimalist look.

---

