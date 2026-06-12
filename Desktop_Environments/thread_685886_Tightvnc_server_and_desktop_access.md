---
title: "Tightvnc server and desktop access"
date: 2008-02-02
forum: Desktop Environments
---

### Post by DanielReidal on 2008-02-02
I have sucessfully installed TightVnc server. If I log in directly to my server desktop (without vnc) I can see Icons (shortcuts) that I have placed there. But when I log in remote to my server I can not see those icons. When I try to drag a icon from the menus, no copy of the Icon is placed on my desktop?

Why?

Cheers ! Daniel

---

### Post by pdc124 on 2008-02-03
because your VNC clinet is connecting to a virtual desktop on your server machine ( thats what the :1) is in the startup .

on your server machine do 
vncviewer localhost :1 and you should get the same desktop that you see when connecting from the remote machine

---

