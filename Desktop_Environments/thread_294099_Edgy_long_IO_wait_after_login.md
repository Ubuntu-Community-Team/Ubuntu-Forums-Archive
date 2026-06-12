---
title: "Edgy long I/O wait after login"
date: 2006-11-06
forum: Desktop Environments
---

### Post by Pedric on 2006-11-06
Hi,

I have upgraded from dapper using the Update Manager. Booting is relatively fast until login. After login (which has a nasty delay when typing my username), gnome splash and interface slowly appear. I have system monitor in my panel, which promptly indicates a 100% cpu load. According to the color of the graph, it's i/o wait, which lasts at least 10s. This also blocks any interaction with the already loaded interface, any commands (such as clicks to the desktop icons) are queued and performed once the i/o wait is done. This is pretty annoying, how can I find out what is causing this i/o wait?

Bootchart and screenshot of system monitor showing the i/o wait after login in attachments.

---

