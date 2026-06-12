---
title: "workspace switching with mouse problem -focus"
date: 2006-08-19
forum: Desktop Environments
---

### Post by ~art on 2006-08-19
I have set up my mouse so that I can switch between workspaces using buttons 6 and 7 using the 'configuring logitech mice' howto using xbindkeys..
[http://www.ubuntuforums.org/showthread.php?t=219894](http://www.ubuntuforums.org/showthread.php?t=219894)

It works when I have no applications running in the current workspace, and sometimes when I have applications running in the current workspace but which are minimized.

I would guess that it is not working because my workspace switching command is being sent to an application instead of x or Gnome.

Does anyone know of a way around this ?
I've tried using keybinding commands and wmctrl to issue workspace switching but I have the same problem of it notworking when applications are running.

 Any ideas anyone ? I'm a Linux noob but I'm not scared of using google so any suggestions welcome.

I really want to be able to switch via mouse rather than keyboard.

Thanks,
art

---

### Post by ~art on 2006-08-20
I set up global_keybindings and keybinding_commands to start system monitor just to check that I was doing it right.
It worked but only when no apps were open or they were minimised.

The keyboard shortcuts work when apps are open but not using the mouse (which uses xbindkeys to issue the keystokes).

It looks like a focus problem where the mose focus's on applications instead of the desktop.

Does anyone have any ideas to get around this.

Thanks,
art.

---

### Post by Bakerconspiracy on 2006-12-28
How did you even bind a mouse button to switch workspaces?

---

