---
title: "Restore xfce menu appearance"
date: 2019-01-19
forum: Desktop Environments
---

### Post by Music_Guy on 2019-01-19
I'm running Ubuntu Studio (which is based on Xubuntu), and I  somehow messed up my applications menu. I had the original menu, with  the favorites on the left side and the applications grouped by theme  (accessories, education, games, internet, etc) on the right hand side.  In installed pitivi from flatpak (I know, I should have installed it  using the synaptic package manager). Now, I still have my favorites on  the left side, but the right side shows only "All". How can I restore  the default xfce menu? (Before and after attached. Before is from a  virtual machine, with no personal favorites added.)

---

### Post by TheFu on 2019-01-19
Create a new userid.  The menu under it will be unmodified.

---

### Post by again? on 2019-01-19
In Xubuntu I have a user config file @ ~/.config/xfce4/panel/whiskermenu-1.rc
Locate this file then move the file and restart panel.
A new user config will be created with system defaults when the panel is restarted.

eg
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] locate whiskermenu-1.rc**
/home/glen/.config/xfce4/panel/whiskermenu-1.rc
```
```
mv ~/.config/xfce4/panel/whiskermenu-1.rc ~/Desktop
xfce4-panel --restart
```

---

