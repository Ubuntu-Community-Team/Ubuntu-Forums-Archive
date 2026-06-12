---
title: "Questions about fluxbox customization"
date: 2008-02-11
forum: Desktop Environments
---

### Post by Hawk__0 on 2008-02-11
Currently, I am running fluxbox in ubuntu (Gnome was getting slow/boring)
I really love the level of customization that can be done, however there are a few things that bother me that im hoping can be answered here :)

1. How do i copy/paste in the terminal?
2. Fonts outside of programs (title bars, tab names in firefox, text on window list, right click menu, etc but NOT inside IM clients, inside terminal, or inside firefox) are extremely small.  How fix?
3. How do i configure transparency on my terminals?
4. Any good site for fluxbox apps?  I would like to stop using pidgin in fluxbox in the hope for a fluxbox IM client..
5. When I click a link in pidgin, it complains about a browser not set up: where can i configure the default web browser?

Thanks!!!!

---

### Post by scxtt on 2008-02-11
1. you can't highlight text w/ the mouse, then use shift+insert? (i assume you're just using **xterm**)
2. that's specific to the theme you're using, you'd have to edit the config for the theme
3. not sure you can, you would have to be using a terminal that has its own transparency, i use roxterm/rox-filer w/ fluxbox
4. fluxbox is just a window manager, doesn't have apps in that sense ...
5. not sure, it used to have a built-in setting for that - hmm ...

---

### Post by Hawk__0 on 2008-02-11
yes using xterm, but i want to copy from firefox into xterm. its not working with sihft insert

edit: it started working =\

---

### Post by Hawk__0 on 2008-02-12
> 2. that's specific to the theme you're using, you'd have to edit the config for the theme
apparently not, i tried many themes... almost all and its always small text
> 4.fluxbox is just a window manager, doesn't have apps in that sense ...
Well, KDE apps look like crap in gnome, thats why i was wondering :)
> 5. When I click a link in pidgin, it complains about a browser not set up: where can i configure the default web browser?
Yeah, odd since it worked in gnome, but not in flux.  i changed it to firefox.

I'd take a screenshot, but i want the screenshot thing mapped to print screen... but dont know how lol

---

### Post by scxtt on 2008-02-12
the thing w/ fluxbox is that it ONLY does what you tell it, so if you don't tell it a general font it defaults to something else ... i don't have flux fired up at the moment (i have it installed as the only WM in Arch) so i can't really get more specific ... if you still can't get the font sizes changed, i'll fire it up later ...

kde uses Qt, gnome uses metacity to define how windows look - they don't always mix and match well - can't really be expected to ... i'm not sure what flux uses, but the less KDE-centric or gnome-centric your apps are, the better visual results you'll get ...

does the link-clicking work now?

---

### Post by Hawk__0 on 2008-02-12
I still can't, here's a pic of what it looks like:

---

### Post by urukrama on 2008-02-12
Have you tried adjusting the font sizes in the theme file (in ~/.fluxbox/styles/THEMENAME/theme.config for themes you have installed or /usr/share/fluxbox/styles/THEMENAME/theme.config for themes installed systemwide)?

---

### Post by urukrama on 2008-02-12
Also, have a look at this thread: [http://ubuntuforums.org/showthread.php?t=280116](http://ubuntuforums.org/showthread.php?t=280116)

Though the thread starter had a different problem, a problem similar to yours is addressed in the thread.

---

