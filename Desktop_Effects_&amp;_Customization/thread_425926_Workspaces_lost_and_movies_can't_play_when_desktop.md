---
title: "Workspaces lost and movies can't play when desktop effects is enabled"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by steliosdjiong on 2007-04-28
hi there, 

just installed ubuntu 7.04, 

i installed codecs for playing .avi and mpeg, when i'm in a normal mode without desktop effects avi and mpegs work just fine, when i start desktop effects(not beryll, just the effects that comes with 7.04) and try to play .avi and .mpeg i get black screens, also now in desktop effects i don't have my workspaces in a cube, i don't even have 4 workspaces...just one(in desktop effects enabled)

please advice

 thank you :)

---

### Post by Cresho on 2007-04-28
those effects are still in development from what I have read.  Install the other ones like beryl and you can disable it when you watch a movie or something gaming.  It needs to be disabled on slower system.

---

### Post by Spin Doctor on 2007-04-28
Hey there. If you are using Totem for playing your movie files. Try this to get them to work when desktop effects are activated.[LIST]
[*]Press ALT+F2
[*]Enter ,"gstreamer-properties"
[*]choose the video tab
[*]At the output line. choose "X Window System (no Xv)[/LIST]You can get multiple workspaces easy with desktop effects. Just right-click on the workplace icon on your bottom panel, and select settings, and just set number of workplaces you want.

---

### Post by steliosdjiong on 2007-04-28
My mistake i din't give you my laptop specs...it's a 1,83Ghz intel dual core, 2gb ram 128 shared intel graphics card

---

### Post by Spin Doctor on 2007-04-28
Did my previous post help you out or still having problems?

---

### Post by steliosdjiong on 2007-04-28
Your post help me do have the videos working in totem while desktop effects are enabled....but when i added the workspaces by right clicking they were like desktop effects disabled workspace, i found a thread helped me have the workspace back by writing in terminal:

```
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
```

Is there anyway i can make VLC working too ?


Thanks :)

---

### Post by CarpKing on 2007-04-29
> **steliosdjiong said:**
> Is there anyway i can make VLC working too ?


Thanks :)

You can go into the preferences and set the Video output module to X11.  Keep in mind that both this and the Totem solution use far more CPU and will get pixelated if you go fullscreen.  If you want to use Xv (the original default) you can install mplayer or gxine, as these seem to handle it better with desktop effects than Totem and VLC.

---

