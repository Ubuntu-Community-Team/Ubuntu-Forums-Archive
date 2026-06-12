---
title: "Beryl Direct Rendering"
date: 2006-11-21
forum: Desktop Environments
---

### Post by DimitrisC on 2006-11-21
I have Dapper installed with Beryl which runs OK.  I noticed that i don't have direct rendering enabled on my ati x300 card which may be the problem why i see choppy animation when i move windows around although the cube animation seems fine.

I get this when i run: $ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_render_texture
OpenGL renderer string: MOBILITY RADEON X300 Generic


The frame rates from glxgears are:

$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
12743 frames in 5.0 seconds = 2542.189 FPS
17269 frames in 5.0 seconds = 3453.799 FPS
17239 frames in 5.0 seconds = 3435.934 FPS
18029 frames in 5.0 seconds = 3590.904 FPS
17214 frames in 5.0 seconds = 3439.437 FPS
17117 frames in 5.0 seconds = 3410.756 FPS
X connection to :1.0 broken (explicit kill or server shutdown).

I don't know if this is normal for my graphics card (Ati mobility radeon x300 128MB on a Dell Inspiron 6000 1.86GHz).

I used this tutorial to install the drivers and beryl.
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/ATI](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/ATI)

Is there a way to enable direct rendering? Will it improve performance?

If not can you please tell me how can i unistall the drivers i have on and install the latest ati drivers (if it will help).

Thanks!

---

### Post by elcyrion on 2006-11-21
Hey, I've got this problem too (cept im using a radeon9800). It works if i fire up xorg without xgl. I'll let you know if i can figure out how to fix this (riiiiight) :)

---

### Post by yatt on 2006-11-21
Try adding:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
to the end of your /etc/X11/xorg.conf

---

### Post by Rajiv_Nair on 2006-11-21
try running the glxinfo cmd without bootin into an XGL session. If it says direct renderin: yes..then i dont think u have a prob. Coz i remember readin somewhere that When XGL uses direct rendering it dosent allow ANY other application to use it which results in all other applications failing to acknowledge that direct rendering exists.

---

### Post by DimitrisC on 2006-11-22
Well i tried glxinfo in a normal gnome session (not xgl) and you were right! It says that i have direct rendering enabled! So i guess its like you said, it works but it cannot be identified.
Thanks! Yous saved me a lot of trouble reinstalling drivers which may not have made a lot of difference! :-)
I even tried glxgears to compare and i have better results in xgl/beryl than i do in a normal gnome session!!! :D

---

### Post by Rajiv_Nair on 2006-11-22
gud to knw:D

---

