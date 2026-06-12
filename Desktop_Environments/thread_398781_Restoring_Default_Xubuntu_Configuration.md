---
title: "Restoring Default Xubuntu Configuration"
date: 2007-04-01
forum: Desktop Environments
---

### Post by _linux_ on 2007-04-01
After messing around with Xubuntu/Xfce, I want to go back to the default configuration (panels, theme, etc.). I've tried uninstalling and reinstalling xubuntu-desktop with aptitude, but the default desktop configuration doesn't come back. Is there a way to do this without formatting?

---

### Post by finferflu on 2007-04-01
Just delete the .config/xfce4 and .config/xfce4-session folders in you home folder ;)

---

### Post by _linux_ on 2007-04-01
Worked good, thanks. The theme and desktop was restored to its default, but the panels weren't. Is there something I can delete to restore that too, or do I have to do it manually?

EDIT: I did the panels manually. My Xubuntu desktop is officially back to default.

---

### Post by finferflu on 2007-04-02
I'm happy it worked for you :)

---

### Post by x1a4 on 2007-04-02
Hi,

The best way to reset all Xfce settings, is to logout, remove the entire ~/.config/ directory, then log back in.  Instead of removing bits and pieces.

---

### Post by fetasushi on 2007-06-04
*The best way to reset all Xfce settings, is to logout, remove the entire ~/.config/ directory, then log back in. Instead of removing bits and pieces.*

All good...but where after you log out do you do this? I removed a couple of the stuff mentioned earlier in this thread and now my 'home' folder has nothing in it except a desktop icon! Me confused.

Hopefully if I can get this extra info re resetting Xfce to get the default desktop all will be ok, as now when I open Firefox, the window can't be seen...it's there but I can't see it so I'm wondering that it's something to do with the panels, except I can't reset them to what they were?

;) Thanks

---

