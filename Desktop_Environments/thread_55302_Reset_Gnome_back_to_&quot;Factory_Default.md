---
title: "Reset Gnome back to &quot;Factory Default?"
date: 2005-08-08
forum: Desktop Environments
---

### Post by senectus on 2005-08-08
I've just swapped back from the Kubuntu to Ubuntu desktop.. and I've made a real mess of my Gnome environment.. any idea's on how I can reset gnome back to the "Ubuntu Factory Default"??

I'm pretty sure it just involves deleting a couple of config files..?

---

### Post by PeP on 2005-08-08
maybe 

% mv ~/.gnome ~/.oldgnome

---

### Post by senectus on 2005-08-09
[QUOTE=PeP]maybe 

% mv ~/.gnome ~/.oldgnome[/QUOTE]
Nope.. didn't make a difference..

---

### Post by bored2k on 2005-08-09
I would try doing that mv trick (or rm) on all hidden folders on $HOME (the ones that start like **.this**). It should work.

---

### Post by ow50 on 2005-08-09
Here's an excessive list of what to rename. Not all strictly Gnome, but closely related. The gnome and gconf directories might alone be enough. Note: untested! Don't delete, but rename. After renaming log out and log back in. Also note that some things, like *GDM login screen* and *users and groups* are global settings.

**directories**
.config
.gconf
.gconfd
.gnome
.gnome_private
.gnome2
.gnome2_private
.local
.metacity
.nautilus
.thumbnails

**files**
.fonts.cache-1
.fonts.conf
.gtk-bookmarks
.gtkrc.mine
.gtkrc-1.2-gnome2
.gtkrc-2.0
.recently-used
.xscreensaver

---

### Post by SKLP on 2005-08-09
I'm not sure about this but don't you need to remove .gconf while not logged in to gnome?

---

