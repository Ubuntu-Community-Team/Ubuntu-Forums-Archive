---
title: "Starting X in fullscreen mode"
date: 2010-11-10
forum: Desktop Environments
---

### Post by pepsifx357 on 2010-11-10
I've installed Ubuntu server just to get the base install.  I was wanting to know, after I've installed Xorg, is there a command that would start it in full screen?

I've tried the geometry option with ```
startx -geometry 1280X1050
```  but it's just a white screen with the terminal at the top left.

When just using startx command by itself, you get a black screen with the terminal in the upper left corner.  When doing this, you have to move the cursor to the top left of the screen to type any more commands.  Any commands you type, the output is in a tiny, confined, box and this is kinda frustrating for me.  

I want X to start with the terminal in fullscreen so that I can run commands and see the output as if I were in the terminal without X.  The reason I want to do this, is so that I can have a "headless" system and still use GUI programs like Firefox.  I'm not worried about window managers yet, as I don't think I need them at this point.

thanks

---

### Post by pepsifx357 on 2010-11-11
bump

---

### Post by cmcx_linux on 2010-11-12
that's the default startup for x. What you need next is a "desktop".. but in order to run a desktop, you also need a window manager. Luckily for you, that, and most graphics card drivers get installed as dependences when you install the desktop. So, go ahead and pick one. 
You have kde,gnome,xfce, e17, fluxbox, matchbox, openbox, blackbox, scrotwm, wmi,twm, which already available in your repo. So go ahead and try some.

---

### Post by pepsifx357 on 2010-11-13
I was trying to figure out how to do this without a desktop environment.  Once I install a window manager the terminal disappears and leaves a GUI environment.  I want a terminal environment that enables me to type a command for a gui program and the program pops up.  Kind of a CLI/GUI type of thing.

---

