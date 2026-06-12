---
title: "Resolution help"
date: 2009-07-18
forum: Desktop Environments
---

### Post by Ubookfanatic on 2009-07-18
I'm new to ubuntu, Im running ubuntu 9.04. My problem is when i restart my computer my resolution changes and makes the screen smaller. the strange thing is this only happens after about two restarts. I have an intel graphics accelerator card. Besides this problem I need to know something, I have 4gb memory but ubuntu only shows 2.8gb is that normal. Any help will be most appreciated.

---

### Post by vinutux on 2009-07-18
**[COLOR="Navy"]System>preferences>display[/COLOR]**

---

### Post by Ubookfanatic on 2009-07-18
> **vinutux said:**
> **[COLOR=Navy]System>preferences>display[/COLOR]**


Yes. Thats what I do when ubuntu reduces my resolution. The problem is after about two restarts the resolution reduces again.

---

### Post by balloooza on 2009-07-19
your two questions:
memory: yes that is normal, you need to use 64bit version to use al 4 GB, but I would either do it now, or never, because you will not want to go through all the setup again.

resolution: you have an intel graphics card, I always have problems with mine too, but the intel should use the default resolution of your monitor, and this should be the optimal, this means that is what your monitor was designed for, resolution is not simply the size of the font, it is accualy the pixils on the screen, you will have a much better experiance by going to system > preferences appearence then take all the fonts from 10 to 13, that will make it bigger (I am guessing that is your problem, if the resolution is not optimal for your display, then just tell me)

The eisest way to change the size of everything is to change the fonts, not the resolution, because resolution will create more problems (like the ones you are having)

---

### Post by Ubookfanatic on 2009-07-20
> **balloooza said:**
> your two questions:
memory: yes that is normal, you need to use 64bit version to use al 4 GB, but I would either do it now, or never, because you will not want to go through all the setup again.

resolution: you have an intel graphics card, I always have problems with mine too, but the intel should use the default resolution of your monitor, and this should be the optimal, this means that is what your monitor was designed for, resolution is not simply the size of the font, it is accualy the pixils on the screen, you will have a much better experiance by going to system > preferences appearence then take all the fonts from 10 to 13, that will make it bigger (I am guessing that is your problem, if the resolution is not optimal for your display, then just tell me)

The eisest way to change the size of everything is to change the fonts, not the resolution, because resolution will create more problems (like the ones you are having)



When i mean resolution I mean when I set it to 1280 X 800 it changes after restart to 1024  X 768.

---

### Post by balloooza on 2009-07-20
Ok, then you need to play around with xorg.conf I belive, I am not by any means an expert on that file, in fact, I never touch, I usualy mess it up, but try this "ubuntu xorg.conf resolution" and see if anyone had the problem, I know there are poeple who know about this mysterious file in the X11 directory, but I am unhelpfull when it comes to this :(

---

### Post by vinutux on 2009-07-20
check xorg.conf file in /etc/X11/xorg.conf .....edit resolution there and save it ([COLOR="Red"]back up original before edit[/COLOR]) ...

```
sudo gedit /etc/X11/xorg.conf
```

---

