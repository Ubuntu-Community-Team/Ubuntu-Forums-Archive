---
title: "Installing new themes"
date: 2011-03-27
forum: Desktop Environments
---

### Post by Ghost_Mazal on 2011-03-27
Lo Guys , I want to install some new themes.

I downloaded some themes from [http://art.gnome.org/](http://art.gnome.org/) and it's zompressed files. When I extract it there is a GTK2.0 folder with all the graphics files in them.

How do you actually install these custom themes ?

Thanx

---

### Post by Copper Bezel on 2011-03-27
Two possibilities. 

To install a theme for all users, open a root Nautilus ( gksu nautilus ) and navigate to /usr/share/themes , then copy the extracted theme folder into that directory. It should just be a folder named for the theme with a GTK folder, a Metacity folder, and an index file.

To install a theme for just your user account, go to Preferences -> Appearance and select the Theme tab, then just drag and drop the whole compressed file right into the Themes selection field. Notice that if you install a theme this way, it won't apply to Root windows like Synaptic or the Update Manager.

Either way, you can apply the theme by finding it in the Theme tab of your appearance settings or apply just parts of it (that is, either the GTK theme or the Metacity theme) by clicking Customize with your current theme selected.

---

### Post by Ghost_Mazal on 2011-03-27
Thank you

---

