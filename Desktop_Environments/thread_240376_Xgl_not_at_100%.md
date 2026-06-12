---
title: "Xgl not at 100%"
date: 2006-08-20
forum: Desktop Environments
---

### Post by waltervalderrama on 2006-08-20
Hello, i tried Xgl. It works perfectly but:

- When i run Xgl alone without compiz, i can watch videos normally at fullscreen, but it is not possible to play at full screen. For example everytime i start UT2004, i play in a small square, whiel without Xgl i used 800 x 600.

- When i start compiz, none of the both things work. When I switch to full screen in a video, it displays horrible, very slow.

I tried 2 Xgl comfigurations in /et/gdm/gdm.conf-custom file

[servers]
0=Xgl

[server-Xgl]
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true

and

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl -fullscreen -br -accel xv:pbuffer -accel glx:pbuffer
flexible=true


What do all those options mean. How can I enable fullscreen acceleration.

Anybody have the same problem???

---

