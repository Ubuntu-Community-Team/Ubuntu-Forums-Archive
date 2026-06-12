---
title: "Default desktop theme managers"
date: 2008-12-25
forum: General Help
---

### Post by chrisbooth12 on 2008-12-25
So I am new to Ubuntu and have been playing around with some themes and stuff but I have ran into a few problems. I have looked at a lot of guides and I think I have done to much to fast. I want to start with a clean slate. Is there an easy way to remove all the "extra" stuff I have installed? The problem I have is when I switch a theme only some of the stuff changes like the title bar but none of the buttons, etc. I think I have conflicting packagers installed like emerald and gtk and stuff like this. Is there way I can check for conflicting packagers or remove everything that I added?

---

### Post by Ivo Moelans on 2008-12-25
When only the window decorations change, that is probably because you are using *System&#8594;Preferences&#8594;Emerald Theme Manager*. This is normal as Emerald is only meant to change the window decorations.
Buttons etc. are changed by *System&#8594;Preferences&#8594;Appearance*. When you click that you are presented with a window that contains all your complete themes. You select a theme by clicking on it. If you must: there is a *Delete* button.
These packages don't conflict but rather complete each other.
Does this make it a little bit clearer?

---

### Post by Ivo Moelans on 2008-12-25
double

---

### Post by chrisbooth12 on 2008-12-25
Well i did a restart and it looks better. I uninstalled emerald. I guess what I really need is some sort of theme guide. Do any exist? The sticky thread helped me somewhat but I am looking for something more complete.

---

### Post by Ivo Moelans on 2008-12-25
This one [http://v1.moblin.org/moblin-wiki/ThemeGuide#head-6b92c140ff3fdff9d817ce42798a636055b441f7]("http://v1.moblin.org/moblin-wiki/ThemeGuide#head-6b92c140ff3fdff9d817ce42798a636055b441f7") is rather complete but technical and covers GTK (Gimp Tool Kit) which themes about everything in Gnome. (Emerald supplements this by giving more elaborate window decoration).
And this, if you haven't found it already, is a good introduction in theming: [http://ubuntuforums.org/showthread.php?t=203093]("http://ubuntuforums.org/showthread.php?t=203093")

---

### Post by chrisbooth12 on 2008-12-25
Ok cool thanks. Can you explain what the difference is between GTK, which is the default theme applyer right? And emerald?

---

### Post by Ivo Moelans on 2008-12-25
Basically Emerald does window borders and nothing else. It only functions in combination with Compiz (the package that a.o. gives you the cube). If Compiz can't be installed or isn't active, window borders are made by Metacity, which can also be themed.
GTK does all the other things: buttons, menus, dialogs... those elements are called *widgets*.
Often you'll find themes that give you a combined GTK + Metacity theme *and* an Emerald theme that all are in the same style. But in Linux you have choice, so you can take a certain GTK theme, combine it with another Metacity theme and yet another Emerald theme. Maybe a little bit confusing in the beginning, but after some time you'll come to appreciate the freedom it gives you to make your desktop your own.

---

### Post by chrisbooth12 on 2008-12-25
Ok I see what you mean. Is there anyways to save the differnt themes for GTK and Compiz and Emerald into a "package" so they can be applied all at once? I still think I have some issues because when I turn off Window Decorcations in compiz i loose my title bars

---

### Post by chrisbooth12 on 2008-12-25
Another question. You have Metacity, GTK and Emerald. What programs control each of these? I see Emerald and Compiz but what about Metacity and GTK? Which of these am I changing in the Theme tab of Apperance Preferences

---

### Post by Ivo Moelans on 2008-12-25
A complete theme is a combination of widgets (GTK) and window decoration (Metacity). If you turn Compiz off (in *Appearance Preferences*, tab *Visual Effects*) that is what you get. If you turn Compiz on your window decorator is inevitably Emerald. Turn window decoration off in Compiz and you get... no window decoration. Why anybody would want to work without window borders I don't know, but hey, it's possible.
To get to know GTK somewhat more push the button *Customize...* on *Appearance Preferences*. *Controls* are essentially the widgets. *Colors*: in some themes you can change the colors of the theme (e.g. *Crux*). *Window Border* is Metacity. And of course you can change your *Icons* and the Mouse *Pointer*.
A theme will define some or all of these elements, but with the tabs you can override these and make your own combination. Let's say you do and you are satisfied with the result. On the main window you can with a push on the button *Save as...* store your theme under a name of your choice.
So, you can easily save as e.g. MyTheme the settings for GTK, sometimes including colors, Metacity, icons, mouse pointer and even your desktop background. But Emerald must be set in *Emerald Theme Manager* an the very many settings for Compiz must be set in e.g. *CompizConfig Settings Manager* (there are others I believe, but this is the 'official').

---

### Post by chrisbooth12 on 2008-12-25
thanks for your help. It appeared I did not have gtkchtheme installed and I do now so I have it figured out. It seemed I am still having display problems but it appears to be a driver issue possibly. I will have to search around for a fix

---

### Post by Ivo Moelans on 2008-12-25
You're welcome and good luck.

---

