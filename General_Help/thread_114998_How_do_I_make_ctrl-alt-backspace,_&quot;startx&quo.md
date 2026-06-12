---
title: "How do I make ctrl-alt-backspace, &quot;startx&quot; give me Gnome instead of XFCE?"
date: 2006-01-09
forum: General Help
---

### Post by majinwu on 2006-01-09
Hi,

I replaced Metacity with XFWM4 (XFCE's default window manager) according to this thread: [http://ubuntuforums.org/showthread.php?t=88393&page=8&highlight=xfce](http://ubuntuforums.org/showthread.php?t=88393&page=8&highlight=xfce)

Then I uninstalled Evolution (bad idea) and messed up my gnome. I reinstalled Evolution and things seemed to be fine after that. However, when I want to restart X by Ctrl+Alt+Delete, then "startx", it sends me to XFCE instead. It used to always send me to Gnome. I tried "startx gnome", but then all I got was an unusable desktop with just a terminal screen open. 

Please help!

---

### Post by soulestream on 2006-01-09
i beleive you edit .xinitrc

and make sure only

exec gnome-session doesnt have a #, in front of it


soule

---

### Post by majinwu on 2006-01-09
What directory should that be under?

---

### Post by majinwu on 2006-01-09
I created a .xinitrc file in my ~ (home) directory with just that line. It brings up gnome now... but my theme is messed up!!
The window border color becomes black even when I change the theme back to the way it was before....

---

