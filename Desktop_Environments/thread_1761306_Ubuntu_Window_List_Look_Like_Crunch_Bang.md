---
title: "Ubuntu Window List Look Like Crunch Bang"
date: 2011-05-18
forum: Desktop Environments
---

### Post by pyro226 on 2011-05-18
I am running Ubuntu 10.04 Gnome 2.  
 

 In the most recent version of Crunchbang, the window list has two panels.  The applications are sorted per virtual desktop, show only icons, and the icons can be dragged across from one group to the other group to change which virtual desktop the application appears in.
 

 How can I make Ubuntu's window list look like the default one in Crunchbang?
 

 Other possible relevant information:  I want to run this on a laptop and still have touchpad tap-clicks disabled.

---

### Post by Copper Bezel on 2011-05-18
Huh. My thought was to say that you can't do this with Gnome Panel, but might be able to with tint2 under Gnome. No such luck, though - tint2 under Metacity only shows windows from the present workspace, and under Compiz, which uses viewports instead, it just shows everything unsorted. 

I don't really see a fix for this. You can replace the application list with DockBar or DockBarX to get windows to display as only icons, but I don't know of anything that sorts by workspace.

Edit: I mean, you *could* use Openbox and have a fully functional tint2 along with all the Gnome services you need. You'd install openbox, select "Openbox Gnome" at startup, and launch gconf-editor, then browse to desktop -> gnome -> required_components and change the key gnome-panel for tint2. Log out, log in, and you'd have Gnome services but Crunchbang's panel and WM. But then, obviously, no Compiz, if you want it.

---

