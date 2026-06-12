---
title: "lost desktop when trying effects...!!??"
date: 2007-04-09
forum: Desktop Effects &amp; Customization
---

### Post by granny6989 on 2007-04-09
I have been running the Feisty release with no problems, on an i686 with an NVidia mx4000. My problem is that I attempted to turn on the 'desktop effects' from the taskbar, and it whites out my screen. Somehow it set itself to default and I can't get it to turn off. I can restart and get to the login page, but if I try to anything besides run the terminal, it goes back to the all white desktop (with just a lost little mouse arrow floating around...). I want to know where to look and what I can reset in the terminal mode to get my standard no 'effects' desktop running again.

Thanks in advance.

S*

:confused:

---

### Post by CyBuzz on 2007-04-09
I would guess that there is a .compiz or .desktopeffects directory with config files in it in your home directory (I am not on my linux box so I cant look) but I would start there.

I had the same problem until I enabled the restricted drivers.  I ESC'ed out though so that saved me

---

### Post by granny6989 on 2007-04-09
yeah not sure where the change is stored ... that's my problem. can't go anywhere in the xwindows environment,  cause it's all white. I think that I hit some 'ok' button or something when it first changed that made the change permanent. now it boots to to the login screen and all that, but as  soon as i log in for a session, it turns all  white with the mouse pointer (working) only.  If i knew where the setting was to change it back through the terminal i could get to it there...

S*

---

### Post by igknighted on 2007-04-10
> **granny6989 said:**
> yeah not sure where the change is stored ... that's my problem. can't go anywhere in the xwindows environment,  cause it's all white. I think that I hit some 'ok' button or something when it first changed that made the change permanent. now it boots to to the login screen and all that, but as  soon as i log in for a session, it turns all  white with the mouse pointer (working) only.  If i knew where the setting was to change it back through the terminal i could get to it there...

S*

Well, you've got a couple options.  You could install and configure the nvidia driver (go to terminal and install "nvidia-glx" then edit xorg.conf), or you could go to the terminal and remove compiz (should just be apt-get remove compiz, if it says it has to remove ubuntu-desktop don't worry, theres nothing in that package).  These are rather blunt force solutions, I would bet theres a config file for it somewhere... i don't know where gnome keeps that stuff tho.

---

### Post by CyBuzz on 2007-04-10
i thruroughly messed up my install trying to figure this out.  the fix was simple though.  Hope it works for you.

It is kind of a broad stroke, but it worked.

at the terminal
> 
mkdir tmp
mv .gnome* tmp/
mv .gconf* tmp/


then restart X and it should be good.  All your Gnome settings will be gone, but it should load 'default' settings.

---

### Post by granny6989 on 2007-04-10
I used your solution Cybuzz, got me back. Thanks so much!!

:popcorn: :popcorn: :popcorn: :popcorn:

---

