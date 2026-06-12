---
title: "Change Program Icon"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by Aikon- on 2008-03-31
I am using the *nuoveXT.2.2* icon theme, which comes with program icons for many common applications. In particular, I am trying to change the Firefox program icon to a custom one that I have here.

The icon I want to use is in a single large PNG, but it appears that the icon theme has several subdirectories with different icon sizes. Is there an easy way I can over-ride the icon theme for Firefox to use the icon that I have?

---

### Post by ad_267 on 2008-03-31
Right click on the icon you want to change and select properties and then click on the icon to change it

If it's in the menu then you need to right click on the menu first and select edit menus then find the program you want and do the same as above.

---

### Post by Aikon- on 2008-04-01
That helps for launchers, but I'm not just talking about that.. I'm talking about the actual *program icon* that shows up in the following places:

[LIST]
[*]Top-left corner of the Firefox window's titlebar
[*]Overlayed on the thumbnails when alt-tabbing etc.
[*]On top of the representative rectangles on the workspace switcher
[*]On the AWN bar (or the regular Gnome taskbar, depending on which I'm using at the time)
[/LIST]

---

### Post by noremac on 2008-04-01
Not to change the subject, but I am having a little issue myself with an icon and didn't feel it needed a new thread just for it. I installed Firefox3 with FF2 still installed. I have now uninstalled Firefox2 and the icon has disappeared. 

I still have icon packs with FF icons but they are not connecting with the new directory of firefox. It was ~./firefox but now is ~./firefox/firefox

I had to ln -s  ~./firefox/firefox /usr/bin/firefox in order to get the command firefox to work again. So I think its cause its in that new directory, they icon is not "connecting" with the command. Such as when its in the panel as a shortcut all I see is the the spring with a metal sqaure on top of it. Not the FF icon. Hopefully that makes some sense...

-C

---

