---
title: "changing resolution from command line"
date: 2006-06-13
forum: Desktop Environments
---

### Post by kreso on 2006-06-13
I like gnome-display-properties application cause I can change my screen resolution without having to restart X.

However, I would, (because of my own sick reasons :) like to change resolutution from the terminal. Does anyone know how to do that?

---

### Post by arejensen on 2006-06-13
Take a look in /etc/X11/xorg.conf.

DefaultDepth    24
SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"

Look for something like that ^

Find the section that matches your DefaultDepth, and your res will be the first entry under Modes. Here it is "1600x1200". Change it to your liking and save. Next time you start X the new res will be used. Type ctrl+alt+backspace to restart X without rebooting.

---

### Post by denkedran on 2006-06-13
try "xrandr" from the commandline

---

### Post by kreso on 2006-06-13
thank you very much! That was exactly what I was looking for :)

---

