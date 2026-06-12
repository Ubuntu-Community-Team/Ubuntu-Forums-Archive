---
title: "Tight VNC"
date: 2006-09-13
forum: Desktop Environments
---

### Post by jasonlfunk on 2006-09-13
I managed to get TightVNC installed on my ubuntu box and when I connect remotely I get the X terminal window. I want to see my desktop and things. I read that typing 'gnome-session' should start it but I'm getting "You're already running a session manager". Ideas?

By the way, I don't use the built in Ubuntu Remote Desktop becuase I'm pretty sure it conflicts with fglrx for some reason. Windows don't refresh and such.

---

### Post by xpavement on 2006-10-31
I added this line to the top of my ~.vnc/xstartup file, and after I could startup the xfce4-session without issues in tightvnc:

unset SESSION_MANAGER

Hope that helps.

---

