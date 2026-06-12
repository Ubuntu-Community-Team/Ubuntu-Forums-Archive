---
title: "[SOLVED] via VNC, no gnome menubars"
date: 2007-09-10
forum: Desktop Environments
---

### Post by teimu on 2007-09-10
Hello

I just got VNC server to run successfully. Just for some background
-the server is started via xinetd,
-gdm starts upon VNC client login on :1 
-"XDMCP" is in this configuration somewhere. I don't know what it does, but the helpful tutorial I read said to utilize it.
-I only have ssh access to this server
-It was a absolute minimal ubuntu install. If there is a package on a traditional install that I might need to use, there is a good chance I _don't_ have it.

The problem however is when I get onto my desktop, I see no menubars. I can't infer if they are even loaded up. 
-It is possible they just may be out range, but even resolution changes in the VNC server arguments (ie "Xvnc -geometry 1280x1024" from 1024x768) and using the clients "fullscreen" feature yield no success. Also, adding more height to the parameter doesnt work, and only adds more desktop.
-Perhaps one of the configuration files I'm using told gnome not to load them up for remote connections?
-Could VNC only be passing the actual desktop, and not menubars? Another interesting behavior is that I can perform tasks that open windows (eg right clicking a text file -> properties), and the titlebar for that window is not shown. I'm sure it's there, I just cant reach it.

Those are all my ideas. I can't think of any other possibilities. Any help is exponentially appreciated.

---

### Post by teimu on 2007-09-10
The problem appeared to be a missing package(s). After an install of ubuntu-desktop, everything is fine, for now =).

---

