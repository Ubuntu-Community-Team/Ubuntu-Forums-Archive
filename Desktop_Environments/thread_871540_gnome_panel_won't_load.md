---
title: "gnome panel won't load"
date: 2008-07-27
forum: Desktop Environments
---

### Post by dpholmes on 2008-07-27
i only have one gnome panel on my desktop, running along with the AWN deskbar.  recently my computer has trouble loading both, sometimes the AWN toolbar shows up as a huge white box, other times the gnome panel shows up as a large white box.  typically if i restart X (ctrl-alt-backspace) and login again, the problem goes away.  today i logged in and my gnome panel was gone, and several ctrl-alt-backspace's did nothing to revive it.  i have no idea how to get the panel back or why it disappeared in the firstplace.  

comp info:
ubuntu 8.04
lenovo t60

---

### Post by p_quarles on 2008-07-27
I am not sure how Gnome starts the panel, but you can restart it mid-session by running
```
gnome-panel
```
in a command prompt. Hopefully, this will cause Gnome to remember that it's there and you won't need to do anything else.

---

### Post by dpholmes on 2008-07-27
when i type that command i get the response: "A panel is already running"

i'd like to reply to the terminal, "no, it's not"

---

