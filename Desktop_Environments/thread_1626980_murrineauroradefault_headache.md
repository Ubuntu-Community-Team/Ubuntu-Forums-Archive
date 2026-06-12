---
title: "murrine/aurora/default *headache*"
date: 2010-11-20
forum: Desktop Environments
---

### Post by KazaRgr on 2010-11-20
hello everybody, for the past 3-4 hours im trying to find out some info on gtk engines on google, but i failed since no article explained in details or was just too old..so here it is:

im using the default (its called "metacity" i believe..?) ubuntu 10.04 engine (also installed CompizConfig Settings Manager to add the Cube and tweak some options) with the ambiance theme..

so the thing is, i wanna install the famous "*elementary theme*" but it requires the Murrine & Aurora engines and i'd like to know if those engines are faster&lighter than the default engine i got and if i install them, will all my CCSM settings -*including cube & multi-desktop function*- **lost, or break** any other functions?

---

### Post by 3Miro on 2010-11-20
You got the terminology mixed up. Metacity and Compiz are window managers, they do effects, window placements, number of workspaces and window decorations. GTK engines write out menus, progress bars, tabs and such. You can run any GTK engine with either Compiz or Metacity.

You install a GTK engines and then you install a theme that uses that engine (you may have an engine installed, but no theme selected, then the engine will not do anything). You can select a theme from System -> Prefs -> Appearance.

Metacity will use the corresponding window decorations (if there are any). By default, compiz will do that as well (gtk-window-decoratior), with Emerald you will have to download a separate emerald theme.

---

### Post by KazaRgr on 2010-11-20
thank you for your fast response, your reply gave answers to a lot of the questions i had with managers/engines and what each one does..i was really confused with all that google-ing :)

---

### Post by 3Miro on 2010-11-20
Go to synaptic and install everything under gtk-engine-something. Then with Ubuntu, you should be able to get any theme out there with either Compiz or Metacity. (theme is scroll bars, progress bars, tabs and menus. What goes around a window is a window-decoration)

For specific window decorations, Compiz + gtk-window-decorator will use Metacity themes (from Gnome-looks and such) and Compiz+Emerald will use fancy schemes. Metacity uses Metacity window decoration schemes only.

---

### Post by koleoptero on 2010-11-22
TO install the elementary themes in ubuntu it's best to use the elementary ppa, which has all that's needed.

Open a terminal and type:

sudo add-apt-repository ppa:elementaryart/elementarydesktop
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install elementary-theme elementary-icon-theme

Then select the theme from the appearance preferences window.

EDIT: And to answer your question about speed, you need to have a very VERY old PC to notice any difference between murrine (which is what the default themes use) and aurora. Plus the elementary theme uses aurora only for a couple of things, and murrine and pixbuf for the rest.

---

