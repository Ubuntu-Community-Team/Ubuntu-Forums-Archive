---
title: "Location of gnome desktop files?"
date: 2009-07-31
forum: Desktop Environments
---

### Post by explainer on 2009-07-31
I wish to migrate my gnome setup to another system, but I don't know where the shortcut files (created by the "Add to Panel" menu item) are located in the file system, nor what they are called.

I also have the same issue for Terminal profiles that I created.  Can anyone point me to them, or some documentation on same?

---

### Post by cariboo on 2009-07-31
All the user's configuration files are in you home directory, thet are hidden, to view the files, open Places-->Home Folder and press Ctrl-h.

---

### Post by VCoolio on 2009-07-31
starters / launchers are in ~/.local/share/applications.
terminal profiles are in ~/.gconf/apps/gnome-terminal/profiles

---

### Post by explainer on 2009-07-31
I found the profiles.  The naming of the folders is a bit odd, but whatever. So thanks for that.

The ~/.local/share/applications folder does not contain anything looking like the launchers I have built and installed on my launch bar.  The only file in the folder is called mimeapps.list, and contains the following:

[Added Associations]
application/x-ssh-key=gedit.desktop;
application/octet-stream=gedit.desktop;
text/plain=gedit.desktop;emacs22-gtk.desktop;geany.desktop;emacsclient-emacs22.desktop;openoffice.org-writer.desktop;
application/x-ruby=gedit.desktop;emacs22-gtk.desktop;geany.desktop;emacsclient-emacs22.desktop;openoffice.org-writer.desktop;
application/x-shellscript=geany.desktop;
x-content/blank-cd=brasero-nautilus.desktop;

How does this relate to a launcher configuration, with Type, Name, Command, Comment, and Icon elements?

---

### Post by VCoolio on 2009-07-31
Sorry, I thought that was where all launchers were stored. Launchers you put on your gnome-panel are in ~/.gnome2/panel2.d/default/launchers.

P.S. the mimeapps.list defines what options you get for opening a file with when you right click it.

---

