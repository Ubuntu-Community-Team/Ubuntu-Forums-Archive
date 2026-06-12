---
title: "No Wallpaper Until Nautilus run"
date: 2008-12-11
forum: Desktop Environments
---

### Post by sexandcyanide on 2008-12-11
When I log in, I have no wallpaper.I have to physically run Nautilus to get the desktop (icons, wallpaper, etc) to show up. Obviously, this is less than optimal.

Why does it do that?

Is there a way to fix the problem?

---

### Post by MCrittenden on 2008-12-11
I get that occasionally, but not every time. If you're getting it on every login, then the easiest solution is probably just to add a session for Nautilus. System->Preferences->Sessions then add an entry for Nautilus (just make the command "nautilus"). That will launch nautilus every time you log in. Hope that helps.

---

### Post by Cyris on 2008-12-11
shouldn't nautilus already be in the starting session at default. you nautilus to view any files and folders. its like trying to use your windows computer without it running explorer.

---

### Post by Vantrax on 2008-12-12
Everything about your desktop is related to nautilus, so if for some reason its disabled you have no luck there at all.

---

### Post by murrayd77 on 2008-12-12
Make sure, you run nautilus command on the system preferences. Once it is done, the wallpaper will appear on every login. 

-- Dave.

---

### Post by Peter09 on 2008-12-12
in a terminal type

```
sudo gconf-editor
```

In the GUI navigate to desktop->gnome->session->required components

Is the filemanager set to nautilus?

---

