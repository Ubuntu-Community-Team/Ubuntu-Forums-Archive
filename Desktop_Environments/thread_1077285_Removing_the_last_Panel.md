---
title: "Removing the last Panel"
date: 2009-02-22
forum: Desktop Environments
---

### Post by DeeVoc on 2009-02-22
I've gone through and searched on this, but all the solutions look to be outdated. They point to going to Preferences->Session->Current and disabling it there, but the "Current" tab is no longer available in the latest version of ubuntu. If anyone can direct me as to how to remove the last panel ( Delete this panel is greyed out for it), I'd greatly appreciate it. Thanks.

---

### Post by mcduck on 2009-02-22
You could try disabling the panel with gconf-editor (press Alt-F2 and run "gconf-editor).

I think it should work id you remove panel from the desktop/gnome/session/required_components_list -key (and possibly unset the desktop/gnome/session/required_components/panel -key).

---

### Post by DeeVoc on 2009-02-22
> **mcduck said:**
> You could try disabling the panel with gconf-editor (press Alt-F2 and run "gconf-editor).

I think it should work id you remove panel from the desktop/gnome/session/required_components_list -key (and possibly unset the desktop/gnome/session/required_components/panel -key).

Unfortunately gconf-editor is flat out ignoring the unset key command. This really feels like something that "should" be easy. I'd be more than fine with just a couple "Are you really sure you want to do this" boxes for removing the last panel than having to jump through all these hoops.

---

### Post by mcduck on 2009-02-22
I just tried this, all I had to do was remove "panel" from the desktop/gnome/session/required_components_list -key and log out. When I logged back Gnome-panel didn't start.

edit: I tried killing Gnome-panel after changing the key but it respawned automatically, so logging out is required before the change has any effect.

---

### Post by DeeVoc on 2009-02-22
I just changed the key to avant-window-manager since that's what I'm using in place of it. Last panel is gone after logging out and back in. Much thanks.

---

### Post by midtown on 2009-05-08
> **DeeVoc said:**
> I just changed the key to avant-window-manager since that's what I'm using in place of it. Last panel is gone after logging out and back in. Much thanks.

Does this actually start awn though? I assume you already had AWN auto-starting so it might just have appeared to work. I tried changing the panel key to gnome-do and removing gnome-do from my autostart, but it didn't start then. I am not sure if whatever is in the key is executed as a command, or how it works.

---

### Post by Athropos on 2009-05-10
Great, thanks for the tip. I'm now using Gnome Do "Docky" and Stalonetray, and I was looking for a way to get rid of Gnome Panel.

---

