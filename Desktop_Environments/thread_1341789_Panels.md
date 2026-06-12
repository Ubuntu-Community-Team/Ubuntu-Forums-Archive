---
title: "Panels"
date: 2009-11-30
forum: Desktop Environments
---

### Post by vamc on 2009-11-30
I am a user of karmic.I installed AWN.So I deleted the bottom panel.I customized the top panel to autohide mode.But the top panel no more comes out of its hiding.I want back both of the panels (no more intrested in AWN).Is there a way to get them back?


Thanks in advance.

---

### Post by psavva on 2009-11-30
> **vamc said:**
> I am a user of karmic.I installed AWN.So I deleted the bottom panel.I customized the top panel to autohide mode.But the top panel no more comes out of its hiding.I want back both of the panels (no more intrested in AWN).Is there a way to get them back?


Thanks in advance.

Right-click on your remaining panel and select "New Panel"; then fill it out with (from left to right): Show Desktop, Window List, Workspace Switcher, and Trash.

---

### Post by fiver22 on 2009-11-30
Can you ctrl+alt+F6 ? This should bring up a terminal, then 
  gconftool-2 --recursive-unset /apps/panel
should reset your panels   -saw this in [http://ubuntuforums.org/showpost.php?p=1426462&postcount=6](http://ubuntuforums.org/showpost.php?p=1426462&postcount=6)
(edit: spelling)

---

