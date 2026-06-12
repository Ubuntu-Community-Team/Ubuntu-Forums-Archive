---
title: "Metacity exhibits annoying 'no visual effect' behavior while using xcompmgr"
date: 2010-11-23
forum: Desktop Environments
---

### Post by murderslastcrow on 2010-11-23
So, I've inherited a pretty interesting blend of computing technology. It's a decent computer for Linux use, but it happens to have a graphics card that's got... half-way support, you could say. It can run OpenGL alright, but it has issues with Compiz and Kwin *teardrop*. So, I decided that if I have to use something other than KDE, I might as well take a spin with Ubuntu again.

Now, the issue is that, if there is a way to get compiz working, I hardly care. I have direct rendering and 3d games, that's all I care about, I don't need things to catch on fire. So right now I'm using xcompmgr so I can still have a compositor and because it can handle fading windows and menus(which I quite admire).

Getting to the point, I obviously don't have compiz on, so metacity is still using its 'no visual effects' settings. This is fine, all but for one niggling issue- the bounding boxes around the windows when they are minimized/restored. They give a very unpleasant effect, but no matter where I look in gconf I can't seem to find a way to turn it off and still keep the regular window behavior. I've been looking around for a workaround but haven't turned anything up so far- if you need pictures/video I can provide it. Thanks in advance for your time in helping me solve this issue.

---

### Post by claracc on 2010-11-23
I have metacity in my gnome desktop without any visual effect in apearance but I can have shadows and elegant borders in windows.

Metacity has its own composition, you run gconf-editor, and in apps --> metacity --> general you can tick in compositing manager. Perhaps in this way the apearance of windows borders would be better.

---

### Post by murderslastcrow on 2010-11-23
Actually, I believe I am using metacity for the window management, so it's not the window borders that have an issue. Xcompmgr offers very nice shadows and smoothness itself, but the main feature I used Xcompmgr over Metacity's compositing for is the fading window animation (for minimizing, opening, closing, etc.).

So the issue isn't with the window borders themselves, but that metacity insists on creating the black box animation for itself when I'm using the xcompmgr animation already during minimization. So I see a fading black box going down to my panel as my window is fading away, which is really annoying and doesn't look good at all.

So my main question is how I can turn off the black box while metacity is minimizing, but still keep everything else the same. There is an option in gconf-editor for low-resource use that gets rid of it, but it also changes a lot of other things like moving windows which make the experience even worse from a design point of view.

I hope I'm being specific enough. Of course, just wondering if any of you know- I'm sure I could just research metacity a bit to find out, but if I were a less advanced user I'd come here first. XD

---

### Post by mcduck on 2010-11-23
> **murderslastcrow said:**
> So, I've inherited a pretty interesting blend of computing technology. It's a decent computer for Linux use, but it happens to have a graphics card that's got... half-way support, you could say. It can run OpenGL alright, but it has issues with Compiz and Kwin *teardrop*. So, I decided that if I have to use something other than KDE, I might as well take a spin with Ubuntu again.

Now, the issue is that, if there is a way to get compiz working, I hardly care. I have direct rendering and 3d games, that's all I care about, I don't need things to catch on fire. So right now I'm using xcompmgr so I can still have a compositor and because it can handle fading windows and menus(which I quite admire).

Getting to the point, I obviously don't have compiz on, so metacity is still using its 'no visual effects' settings. This is fine, all but for one niggling issue- the bounding boxes around the windows when they are minimized/restored. They give a very unpleasant effect, but no matter where I look in gconf I can't seem to find a way to turn it off and still keep the regular window behavior. I've been looking around for a workaround but haven't turned anything up so far- if you need pictures/video I can provide it. Thanks in advance for your time in helping me solve this issue.

There's a little gconf trick that allows you to do exactly that.

- press Alt-F2 and run "*gconf-editor*".

- Browse to *apps/metacity/general* and enable the "*reduced_resources*"-key. This will remove the ugly animations while minimizing/restoring a window. On the other hand it will at the same time add another ugly wireframe animation, replacing the window contents when resizing a window. Which is the reason for the next step:

- Browse to *desktop/gnome/interface* and enable the "*accessibility*"-key. Your window contents should now once again show when resizing a window, while all ugly animations are gone. :)

---

### Post by murderslastcrow on 2010-11-23
Thank you very much! I had located the reduced_resources option, but the grid really didn't sit well with me, so I'm glad you came to my rescue. Thank you for sharing your knowledge with me- now I have a flawless yet light resource composited desktop. :D

---

