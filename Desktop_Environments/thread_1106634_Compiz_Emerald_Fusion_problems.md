---
title: "Compiz Emerald Fusion problems"
date: 2009-03-25
forum: Desktop Environments
---

### Post by tonyW303 on 2009-03-25
so when I download and import an emerald theme into the emerald manager,  it applies.... sorta.. the border of my windows change to the theme but everything else stays the same.. help? also when im running the emerald manager (the actual GUI) my computer is <beep> slow! is there anything i can do to speed that up? ALSO should i have "compiz --replace" AND "emerald --replace"? or just one? if so which one? thanx!](*,)

---

### Post by mcduck on 2009-03-26
Emerald is only responsible of your window borders. It has nothing to do with what's going on inside the window. To change how your applications look like you need to change your GTK2 theme.

I also find the Emerald Theme Manager quite slow, as fat as I know there's nothing you can do about it. Of course not having too many themes installed helps a bit.

What comes to "compiz --replace" and "emerald --replace", where you have those? To use Compiz, the best way is to enable the desktop effects from the menu. This way your system loads Compiz directly, instead of first loading Metacity and then replacing it with Compiz.

..and to use Emerald as window decorator you should configure it in Compiz settings (same reason as above, you don't want to load something and replace it with something else when you can load the right thing in the first place). The correct place is the Window Decoration-plugin, just change the decorator to /usr/bin/emerald.

---

