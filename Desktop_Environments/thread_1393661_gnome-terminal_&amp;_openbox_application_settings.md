---
title: "gnome-terminal &amp; openbox application settings"
date: 2010-01-29
forum: Desktop Environments
---

### Post by covertcj on 2010-01-29
Hi,
I have an openbox desktop set up and am looking to put a terminal in the corner that has no border, title, etc.
I have managed to get everything working except for the removal of the window decorations. I have been trying to use the rc.xml in the openbox configurations, but can't find a way to uniquely identify this specific terminal window. I have tried to use commands such as:
```
gnome-terminal --geometry 80x24-22-54 --profile=dock --hide-menubar --role="DockTerminal"
```or
```
gnome-terminal --geometry 80x24-22-54 --profile=dock --hide-menubar --name="DockTerminal"
```but these do not seem to work.

Does anyone know how I might go about resolving this issue?

Thanks,
Chris

---

### Post by Megafag on 2010-01-29
> **covertcj said:**
> Hi,
I have an openbox desktop set up and am looking to put a terminal in the corner that has no border, title, etc.
I have managed to get everything working except for the removal of the window decorations. I have been trying to use the rc.xml in the openbox configurations, but can't find a way to uniquely identify this specific terminal window. I have tried to use commands such as:
```
gnome-terminal --geometry 80x24-22-54 --profile=dock --hide-menubar --role="DockTerminal"
```or
```
gnome-terminal --geometry 80x24-22-54 --profile=dock --hide-menubar --name="DockTerminal"
```but these do not seem to work.

Does anyone know how I might go about resolving this issue?

Thanks,
Chris

[This]("http://crunchbanglinux.org/wiki/howto_have_terminator_become_your_wallpaper") might be helpful, but its kinda dependant on terminator and crunchbang...

---

