---
title: "Gnome's window borders got HUGE"
date: 2007-04-11
forum: Desktop Environments
---

### Post by kristjans on 2007-04-11
Why they got so huge and *how can it be fixed*?
A screen-shot tells more than a thousand words ;)
[http://img386.imageshack.us/img386/504/ubuntuforumspq8.png](http://img386.imageshack.us/img386/504/ubuntuforumspq8.png)

---

### Post by ComplexNumber on 2007-04-11
hmmm they should be the size shown in the screnshot shouldnt they? is the metacity theme called GiloucheIM?

i wonder if its a screen resolution issue (ie its set too low). its not just your windows borders that are huge - the text and some of the widgets seem huge too.
EDIT: probably not.

---

### Post by kristjans on 2007-04-11
Thanks for your input. They we're smaller before restart. And they are huge for any window borders that I can select. :( 

BTW what theme are you using? I like the button shading.

---

### Post by ComplexNumber on 2007-04-11
> **kristjans said:**
> Thanks for your input. They we're smaller before restart. And they are huge for any window borders that I can select. :( 

BTW what theme are you using? I like the button shading.
i made the gtk theme myself :mrgreen:. its nothing special at all - merely a colour mod of Murrina-ColOrange. i make lots of colour mods for  themes that i like. it was originally orange, so i made a blue, sky, olive, green, lime, brown, turquoise, red, yellow, violet, cobalt, scarlet, and sunset version of it. i think you'll like the murrina engine and the themes that are made using it. its the most configurable engine of all and most have them have those button 'highlights'.

as for your problem. have you tried just rebooting? maybe its a glitch of some sort.
also, were they ok when you were last logged in? and did you do anything significant which may have changed anything?

---

### Post by kristjans on 2007-04-11
Nice. I'll check it out later once the problem is fixed. Might it be that I installed "FontForge"? I have no idea what that application does, but when I tried to compile Wine it said that it could not do something because it wasn't installed. I wanted more features, therefore I installed it.

Also, I did a full upgrade, changed some symlinks that had to do with installing wine, and more less important changes.

**[color=red]e1:[/color]** The fonts look ugly too now. I just remove FontForge and see what happens, because Wine failed to compile anyways.
**[color=red]e2:[/color]** Removing FontForge didn't help. I'll try the older kernel.
**[color=red]e3:[/color]** Using the old kernel didn't help. I'll try to find out what symlinks I have changed.
**[color=red]e4:[/color]** Here's the guide that I followed:
> This next part worried me a little bit when the Wine wiki said to do it; here you make symbolic links for your 32-bit library files, but I already had these symbolic links pointing to other files. I&#8217;m not sure where the existing links came from, but I just wrote over them.

cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so[http://www.ilfilosofo.com/blog/2007/01/12/installing-wine-on-ubuntu-edgy-610-64-bit/](http://www.ilfilosofo.com/blog/2007/01/12/installing-wine-on-ubuntu-edgy-610-64-bit/)

---

### Post by kristjans on 2007-04-12
BUMP (I edited my previous post)

---

### Post by kristjans on 2007-04-12
It got even worse now. When I start up Gnome, it says that a gnome panel is running already. I get no gnome panels and no wallpaper. I'm posting this off Enlightenment window manager...

---

### Post by ComplexNumber on 2007-04-12
i would probably find it quite difficult to locate the source of the problem now. but it may point to something thats gone awry in your personal settings. its probably no biggie - just create a new user account and move all your files and documents over there (don't move system directories such as .gconf, gconfd, .nautilus, metacity, .gnome2, etc. you can move applications such as .tomboy, .mozilla, etc if you have lots of customisatin and settings that you don't want to redo. don't forget to add the new user to the admin group just after you've created the new user account.

---

### Post by kristjans on 2007-04-13
I moved to Ubuntu Feisty beta, so I cannot really tell if it would work. But thank you, at least I know what to do if something like that will happen again.

---

