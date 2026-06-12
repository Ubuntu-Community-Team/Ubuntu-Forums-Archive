---
title: "Banshee doenst recongize iPod when usind LXDM"
date: 2010-07-10
forum: Desktop Environments
---

### Post by JesusMcCloud on 2010-07-10
banshee recognizes my ipod /but also other media players just fine when i use gdm as my display manager, but when i switch to lxdm (without changing any statrup services in my Xsession) no mediaplayer gets recognized unless i disable automount in nautilus.

this behavior is reproducable on 4 system, here are the current configurations:

System1 (laptop):
[LIST]
[*]lxsession as session manager
[*]nautilus as file manager+desktop
[*]avan-window-navigator
[*]gnome-panel
[*]compiz
[/LIST]

System2 (laptop):
[LIST]
[*]lxsession as session manager
[*]nautilus as file manager+desktop
[*]avan-window-navigator
[*]compiz
[/LIST]

System3 (box):
[LIST]
[*]lxsession as session manager
[*]nautilus as file manager+desktop
[*]lxpanel
[*]openbox
[/LIST]

System4 (box with archlinux):
[LIST]
[*]gnoem session as session manager without any fiddling around
[*]nautilus as file manager+desktop
[*]avant-window-navigator
[*]gnome-panel
[*]compiz
[/LIST]


gdm has to use some magic i cannot fidn in any config file to start up soem deamons needed for banshee in order to recognize portable media players

which is it?

the only warning i get when i start banshee with --debug is that multimedia keys dont work (on the 3 systems not using gnome-settings-daemon)

---

