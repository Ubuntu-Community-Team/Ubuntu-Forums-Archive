---
title: "Moving the workspace overview in Activities to the left"
date: 2018-11-03
forum: Desktop Environments
---

### Post by Pablo_San_Martn on 2018-11-03
Is there any way of moving the workspace overview in Activities to the left side of the screen, without losing the grid representation of [Workspace to Grid]("https://extensions.gnome.org/extension/484/workspace-grid/")? I've tried looking for extensions or and going through the Gnome Tweak tool, but without success.

Having used other DEs in the past (Unity, Xfce, KDE), I am used to efficiently moving the pointer around the top left corner of the screen only, and find it quite annoying to have to move all the way to the top left to the middle right to select a workspace, after launching Activities using the hot corner.

---

### Post by mc4man on 2018-11-03
You won't be able to move it & keep grid. What's wrong with super key?

---

### Post by Pablo_San_Martn on 2018-11-03
> **mc4man said:**
> What's wrong with super key?

Nothing really - only that I sometimes use keyboard commands (e.g. to launch activities and move between workspaces) and sometimes I use the mouse, depending on the kind of task I'm undertaking.

---

### Post by mc4man on 2018-11-04
If you are using xserver (default), not wayland, you could install xdotool & then create a launcher on the desktop that would expose the dash
Something like - 
```
sudo apt install xdotool
```
```
gedit Desktop/wss.desktop
```

```

[Desktop Entry]
Version=1.0
Name=WSS
Type=Application
Terminal=false
Icon=
Exec=xdotool key super
```

After creating launcher right click on wss.desktop > Properties > Permissions & set it to be executable. Then on 1st double click accept the trusted nonsense.., ect.
If a specific icon is desired add to Icon=line , full path is usually best. Name= can be anything you want.

---

### Post by Pablo_San_Martn on 2018-11-04
That's a good idea - thanks!

---

