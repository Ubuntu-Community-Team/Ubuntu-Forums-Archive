---
title: "&quot;Displays&quot; System Settings for All Users"
date: 2011-12-14
forum: Desktop Environments
---

### Post by Charlotte18 on 2011-12-14
Does anyone know how to set the displays settings that appear in "System Settings > Displays" so that the settings apply to all users and not just to the current user? I'm trying to do this in Ubuntu 11.10 (Unity).

---

### Post by thaelim on 2011-12-16
The way to do this is to place a script in /etc/X11/Xsession.d that sets up the screens as desired. This will run for all users on login and set up the screens accordingly.

---

