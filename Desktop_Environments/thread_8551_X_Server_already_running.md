---
title: "X Server already running ?"
date: 2004-12-18
forum: Desktop Environments
---

### Post by vaskark on 2004-12-18
I just started Warty and received this message:
   
   There already appears to be an X server running on display :0
   
   The [full message]("http://www.hwcn.org/%7Eaq200/xserver.jpg") gives me 2 choices (yes/no), yet both don't seem to bring me to my GDM login screen. Can anyone suggest a solution? I'm n00b. Thanks.

---

### Post by Roland77 on 2004-12-18
said as a browsing n00b on these forums ; I have the same problem...

After following most of the advice on these boards and the EXCELLENT complete ubuntu setup guide, My Xserver kept on crashing too :(

First time updatin sources.list with the hoary files, upgraded it too X11, which never started, second time I only used the Hoary stuff for utility updates (like firefox 1.0) and used the stable warty files for a system update with apt-get, same crash occured...
Today I tried to install it all again, but after a fresh install of ubuntu warty and a update with the warty files it all crashed again :(
I should mention I use a Thinkpad T21 for it, somehow I cant get Xwin to do what I want...

Maybe ur problem lies in using the unstable hoary files ? worth a look..
Since I had similar errors using only warty files I'm kinda lost too...

Good luck.
gr. Roland

---

### Post by vaskark on 2004-12-18
I'm not sure why this happened. Things were fine on warty for me until I did an update a few days ago, and now this xserver snag. I also have a hoary system (i love virtual pc!) and things are working over there (mostly).

---

### Post by nemin on 2004-12-19
I had the same problem with X. I now use some sort of "workaround" which works fine for me:
Login using the commandline (press Ctrl+Alt+F1) and remove /tmp/.X0-lock. Then enter startx.
It's not a fix of the problem, but I can live with it :)

---

### Post by vaskark on 2004-12-19
K, i logged in at a terminal and deleted /tmp/.X0-lock, then ran startx and was sent into GNOME. Awesome! I guess this'll be alright for now. But I notice that it skipped the GDM. Was this because I switched to a terminal to login?

---

### Post by nemin on 2004-12-19
[QUOTE=vaskark]K, i logged in at a terminal and deleted /tmp/.X0-lock, then ran startx and was sent into GNOME. Awesome! I guess this'll be alright for now. But I notice that it skipped the GDM. Was this because I switched to a terminal to login?[/QUOTE]
Yeah, it's clear the problem is GDM. Downloading the latest GDM worked for me :) So type: 
sudo apt-get install gdm

Think that will fix it :)

---

### Post by vaskark on 2004-12-20
>  Yeah, it's clear the problem is GDM. Downloading the latest GDM worked for me :) So type: 
  sudo apt-get install gdm  I tried that, but I already have the latest gdm! Should I remove then re-install?

---

### Post by nemin on 2004-12-20
[QUOTE=vaskark]I tried that, but I already have the latest gdm! Should I remove then re-install?[/QUOTE]
hmm, that's strange! You could try to reinstall GDM, but I'd not expect too much of that.. Good luck!

---

