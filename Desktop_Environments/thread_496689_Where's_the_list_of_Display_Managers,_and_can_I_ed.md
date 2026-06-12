---
title: "Where's the list of Display Managers, and can I edit it?"
date: 2007-07-09
forum: Desktop Environments
---

### Post by OzzyFrank on 2007-07-09
Just wondering if there is an actual file that holds the list of desktops that you can choose from at the login window. If there is a file, I assume I can edit it, so the real question is if there isn't one, can I edit the list of sessions somehow? I would like to edit the list not to delete things (I'd uninstall them if that were the case) but to change the order around.

---

### Post by john.nicholls on 2007-07-10
If you're using gdm, does /etc/gdm/gdm.conf give you what you want?

---

### Post by OzzyFrank on 2007-07-11
No, didn't think it was that easy, but a good enough guess considering I do use gdm. I gather the list would be the same using kdm or another, so they all have to be able to access it. I'll have to do some poking around I guess. I'll post what I find.

---

### Post by bonzodog on 2007-07-13
for the list of available sessions, look in /usr/share/xsessions.

In there, you will see a list of .desktop files that match the installed window managers.

---

### Post by OzzyFrank on 2007-07-13
Yeah, that looks to be the most likely place, and I gather deleting one will make it disappear off the sessions list at login. If I want to remove a desktop environment I'll of course do it the correct way, but a couple of them put unneeded additional entries, for example "FVWM" and "FVWM-Crystal" (both seem exactly the same).

---

