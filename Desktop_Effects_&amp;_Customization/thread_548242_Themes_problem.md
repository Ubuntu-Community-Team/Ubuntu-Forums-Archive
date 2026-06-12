---
title: "Themes problem"
date: 2007-09-11
forum: Desktop Effects &amp; Customization
---

### Post by antario91 on 2007-09-11
I will try my best to describe my problem. As you can see on my screenshot, when I apply a theme with emerald, or even with GTK, the theme will only apply to the decorator of a window, and not the window itself, so I get an ugly frame, and it doesn't fits to the window. I saw pictures on [http://gnome-look.org](http://gnome-look.org) and they look more beautiful than mine. (I hope you got my point) Here are my pictures:
Screenshot
[[IMG]http://img392.imageshack.us/img392/2389/screenshothe5.th.png[/IMG]](http://img392.imageshack.us/my.php?image=screenshothe5.png)
Neat-looking (not mine, but desired)
[[IMG]http://img458.imageshack.us/img458/9347/618491zp3.th.jpg[/IMG]](http://img458.imageshack.us/my.php?image=618491zp3.jpg)

---

### Post by 1337455 10534 on 2007-09-11
My opinion is that you should uninstall Beryl and go with Compiz Fusion. It is almost always more stable.
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by smartboyathome on 2007-09-11
Emerald is simply a window manager, and doesn't have anything to do with anything other than the window borders. You would need the GTK file installed on your system and to choose it as your controls in either System>Preferences>Theme (Fiesty and before) or System>Preferences>Appearance, and then selecting Customize.

---

### Post by antario91 on 2007-09-12
I don't understand... I have GTK installed, and it is still the same.... :(
I try to install compiz-fusion...
compiz-fusion installed, no change...

---

### Post by the yawner on 2007-09-12
Emerald is only responsible for drawing the window borders (as smartboyathome pointed out). For you to be able to get something similar with that on the 2nd screenie, you'll need to install a GTK theme that would complement your window borders/decorations. The GTK theme is responsible for the appearance of the scroll bar on that picture, along with the gray metallic texture inside the windows' surfaces. And you can't do this anywhere in Compiz. You just need to edit your default theme under Preferences (if you're using Ubuntu).

---

### Post by FuturePilot on 2007-09-12
Emerald is only responsible for the window decoration. What you're looking for is a Gtk theme. There's plenty to choose from here
[http://www.gnome-look.org/index.php?xcontentmode=100]("http://www.gnome-look.org/index.php?xcontentmode=100")

---

### Post by antario91 on 2007-09-13
If I apply a GTK theme, it is all the same, the window border remains "Human"

---

### Post by 1337455 10534 on 2007-09-19
this is a Guess:
Alt+F2
and run:
ccsm

then using search filter or w/e find "Window Decoration"
for the command, type "gtk-window-decorator"
and reboot if it doesn't work immediately

---

### Post by Newbie1978 on 2007-10-02
I use this simple steps and bingo! got it to work pretty quick I may add, it seems so simple now but sure I have a lot of frustration while trying to get it up and running

Type on a terminal:

sudo aptitude install emerald emerald-themes

compiz --replace emerald

---

