---
title: "Gnome Workspace Switcher + Beryl"
date: 2007-02-18
forum: Desktop Environments
---

### Post by sysctl on 2007-02-18
Hi,

I can't get my head around how workspace switcher works in Gnome with Beryl. Currently I have **1** workspace configured in workspace switcher applet, but I have **6** desktops (or workspaces?), when I choose more than one, I have the correct number of workspaces in the applet, but when I switch, the applet doesn't change. It is like every workspace contains **6** desktops and I switch between them (Ctrl+Alt+Up/Down). I checked, it is specific to Beryl (is that a feature?).


How to get rid of this behaviour and have it the same way as with Metacity? (I am using the latest Edgy and Beryl 0.1.9999.2)

---

### Post by mcduck on 2007-02-18
The difference is that the applet in Gnome panel handles workspaces, whereas Beryl/Compiz uses viewports. This is required for the cube thing to work at all. So you have 1 workspace that contains as many viewports as you configure in Beryl settings. You could also add second workspace, resulting in 2 separate cubes.

The applet in Gnome doesn't currently support viewports so there's nothing you can do about it.

---

### Post by sysctl on 2007-02-18
Oh well. Anyway, found it. Makes sense now, thanks.

---

