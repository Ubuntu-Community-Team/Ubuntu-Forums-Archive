---
title: "Making a GNOME Theme"
date: 2011-06-08
forum: Desktop Environments
---

### Post by ATMSTopo28 on 2011-06-08
Hey everyone, I'm relatively new to Ubuntu (using it since 10.04) and I have a question about the GNOME desktop environment. I would like to create my own full desktop theme (like Ambiance) and not just rely on Ubuntu tweak and other applications. I've looked on online resources (such as the GNOME live tutorials) and some of the code presented is rather confusing. I have some coding experience, but the GTK+ and other associated files are  new territory for me. 

Any help would be appreciated! :)

---

### Post by sanderd17 on 2011-06-08
What kind of theme do you want to make? A gnome-shell theme or a GTK+ theme?

for the first one, you can look here [http://live.gnome.org/GnomeShell/Development](http://live.gnome.org/GnomeShell/Development) (at the bottom of the page)

if you want to create a gtk+ theme, look here [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes) Maybe it would be good to search the code of a theme that comes close to what you want and adapt that code.

FYI: gtk+ themes are still used in gnome-shell to change the look of the windows and the inner side of the windows. gnome-shell themes are made to change the look of the activities window and the panel.

---

### Post by ATMSTopo28 on 2011-06-08
Thanks for the help. I wanted to make a theme that can be downloaded (such as from GNOME-art) and simply select it from the theme part of the appearance preferences selection in the "change desktop background" menu. It seems like its a combo of GTK+, Metacity, and the other suggestions you've mentioned. I've just seen all the cool desktop themes from OMG! Ubuntu and other places and I've always wondered how to do it, but it seems like a pretty tedious hack. I was looking for some advice before I proceeded :)

---

### Post by Copper Bezel on 2011-06-08
There's not a lot of documentation, but you can take any theme you like, copy the folder, and make the changes you want or simply replace everything. A Gnome 2 theme is essentially a mix of text configuration and image files, and they can all be edited directly. One thing that might help as you progress: try out the command metacity-theme-viewer [Your Theme Name].

---

### Post by jerrrys on 2011-06-08
i did my own with gimp

[ATTACH]194577[/ATTACH]

---

### Post by ATMSTopo28 on 2011-06-08
Thanks for all the suggestions. The metacity-viewer suggestion is really helpful to view results of Metacity edits. I guess my real question is more of GTK's and Metacity's syntax in the code itself more so than the overall structure of the theme. I know the documentation is pretty thin but if anyone can guide me to a really good overview of both then it would be appreciated!

---

