---
title: "Desktop effects working but windows are blank"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by gashcr on 2007-04-28
Hi, my problem is as follows. 

When I activate desktop effects on feisty, everythink runs fine, when I restart, five things happen:

Main menu items don't get highligthed when mouse-over them...
Windows get blank until I maximize or minimize or resize them... 
If use nautilus and enter a directory, the screen does't refresh and I get the same content until I maximize or resize...
Icons dissapear from desktop until I activate them...
I don't get video playback on the thumbnailer (Alt-tab)

I have a radeon 9250pro 256M
I thought adding Option AddAGBGLXVisuals true to the xorg would solve it, but it remains the same.

What do you think could be producing this??

Thanks

---

### Post by gashcr on 2007-04-30
OK, I realized this only happens when I logoff and then open session again... pretty weird, must be some buggy stuff... Everything solves if I restart xserver... Is there a way to tell the system to restart xserver when closing sessions??

Anyway, I still don't get video playback...

I need your help guys!!

---

### Post by gashcr on 2007-05-01
OK, got it, at least the video playback...

Only needed to change the gstreamer-configuration, video-output to x window system (no xv). I found that in other post and gave it a try. 

Concerning the blank windows... I can live without closing my session, jaja.


So you can this thread is SOLVED

---

### Post by jgruber on 2007-05-25
You can fix your logout/login problem by changing your /etc/X11/xorg.conf file adding this to your Device section for your video card.  

Option          "XAANoOffscreenPixmaps" "true"

It worked like a champ for my Intel Corporation Mobile 945GM card which was having the same issue.

John

---

