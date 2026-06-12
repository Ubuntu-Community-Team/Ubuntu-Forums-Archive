---
title: "Windows launch with toolbar off screen"
date: 2006-06-22
forum: Desktop Environments
---

### Post by dan.imbrogno on 2006-06-22
Hi there, I just installed XGL+compiz and it is working nicely. But ever since the install, whenever i launch an application, its toolbar (title bar, minimize, maximize and close buttons) is positioned above the top of the screen, underneath the GNOME panel. If i want to get to these buttons i have to alt + click every application i launch and move it down. How can I fix this? 
Is there a configuration setting somewhere that sets the default X and Y coordinates for launched aps?

---

### Post by dan.imbrogno on 2006-06-24
I fixed this problem.

I had installed ATI drivers because i didn't think I had 3D acceleration enabled after installing ubuntu. These ati drivers were crap and caused a lot of issues. Upon reinstalling ubuntu i realized that my ATI 9700 radeon mobility card in my Dell Inspiron Laptop supported 3D acceleration out of the box! So i simply installed XGL and it works a million times better now.

---

### Post by karlsson88 on 2006-06-24
i have the same problem, do you now how so solve it? without reinstall everyting? it worked for me for a while, then the windows started to be like yours, openeing outside the screen, maby it is something in the gconf-editor ?

---

### Post by dan.imbrogno on 2006-06-24
I'm not totally sure. I think it's an issue with improperly configured video card drivers / 3d acceleration support.

I'm very new to linux so i don't want to offer any advice because i barely know what i'm doing still :)

hopefully someone with a bit more experience can help us out.

How can you tell if 3D acceleration is enabled?? XGL works fine, but when i start playing video files it slows to a crawl, and i cant get the command fgl_glxgears to work. i get the error:

Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig

I'm thinking maybe i don't natively have 3d support as i originally thought

---

### Post by hegenious on 2006-06-24
could you run the command "glxgears" successfully?

---

### Post by dan.imbrogno on 2006-06-24
yep i can. i get in between 3000 and 6000 fps

---

### Post by superhew on 2006-06-24
can't really offer any advice here, i also have the same problem. i am using nvidia drivers, and have scoured gconf-editor and found nothing in relation to compiz/xgl. if anyone has a solution to this problem, it would be much appreciated. i want to say it has something to do with the window manager, but i don't know for sure.

---

