---
title: "Can not resize autohide size for Gnome Panel in Gutsy"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by bobsacks on 2007-10-19
I just upgraded to Gutsy from Fiesty and I am having problem with the gnome panels. On fiesty I would go into the gconf-editor and then change the values of Apps - Panel - default_setup - toplevels - bottom_panel - auto_hide_size to 1 and when I would reboot it would work fine. It is not working properly in Gutsy. I have even changed the global keys to 1 and nothing is happening. 

Has anyone else had this problem? Am I changing the right key? Is there a way to go in through the console and manually edit a file somewhere to get this to work?

Thanks

---

### Post by Tamale on 2007-10-21
I am having the same problem.

---

### Post by Evilgiraffe on 2007-10-24
Try changing the key in (panel - toplevels - bottom_panel_screen0 - auto_hide_size)

---

### Post by bobsacks on 2008-02-27
I found my solution. The proper attributes to edit inside gconf-editor are found under - Apps - panel - toplevels instead of default_setup

---

