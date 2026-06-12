---
title: "Compiz Fusion crashes if I open more than 165 windows?"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by ikkefc3 on 2007-10-17
If I open 165 or more windows (e.g. Thunar), Compiz Fusion + X crash and I come back at the login screen, is this a bug or something?

---

### Post by bromix on 2007-10-17
Yikes, i dunno what I would do if I had 165 windows open at same time.  I could never manage that.

---

### Post by cudaman73 on 2007-10-17
Wow.

How do you ever have 165 windows open?

That's a ridiculous amount :O

---

### Post by Rupertronco on 2007-10-17
I can't ever imagine a use for that many windows,  but I'm guessing it's exceeding your graphics capabilities, rather than compiz bugging out. 

What are your system specs?

---

### Post by bromix on 2007-10-17
thanks guys, glad you posted that too, I sorta felt bad, but my goodness!

---

### Post by Lozz on 2007-10-17
I should think you'd be hard pushed to find any window manager that would survive that. Like all the others I will have to ask, out of curiosity, what is it that one does with 165 windows?

---

### Post by ikkefc3 on 2007-10-17
> **Lozz said:**
> I should think you'd be hard pushed to find any window manager that would survive that. Like all the others I will have to ask, out of curiosity, what is it that one does with 165 windows?
The task that needs 165+ windows: remembering yourself why you bought an Intel C2D processor (and prooving that PC's are faster than macs for the same money).

My system specs:
- Intel Core 2 E6400
- Asus P5B-VM motherboard
- 2GB RAM (DDR2_800 CL4)
- nVidia Geforce 7600GT
- Samsung SP2504C 250GB SATAII Harddisk
My system doesn't feel like it runs out of resources.

With the XFCE  standard window manager I can easily open around 500 windows (50 divx videos + 175 mousepads + 175 thunars + .100 pictures in the GIMP).

---

### Post by Rupertronco on 2007-10-17
Well compiz certainly takes more resources to manage windows than xfce does, but with those specs you shouldn't run into a problem. Are you just trying to see how much random stuff you can open before your system crashes? I find that to be a pointless endeavor, but I guess you could start by telling me if you're using gutsy or feisty  and what compiz packages you have installed....

```
dpkg -l | grep compiz*
```

I don't seem to have a problem with opening more than 165 windows, although I find it useless to have that many open.

50+ Divx movies? You're completely incapable of interpreting more than 3 of them at a time, what's the point? I'm not going to spend time trying to discover the source of the problem if this has no real application.

---

### Post by ikkefc3 on 2007-10-17
> **Rupertronco said:**
> Well compiz certainly takes more resources to manage windows than xfce does, but with those specs you shouldn't run into a problem. Are you just trying to see how much random stuff you can open before your system crashes? I find that to be a pointless endeavor, but I guess you could start by telling me if you're using gutsy or feisty  and what compiz packages you have installed....

```
dpkg -l | grep compiz*
```

I don't seem to have a problem with opening more than 165 windows, although I find it useless to have that many open.

50+ Divx movies? You're completely incapable of interpreting more than 3 of them at a time, what's the point? I'm not going to spend time trying to discover the source of the problem if this has no real application.
I'm running Ubuntu Gutsy with the official Ubuntu packages, but I had the same problem in version 7.04,
dpkg -l | grep compiz* gives:
```
ikkefc3@compaqcaspi8000:~$ dpkg -l | grep compiz*
ii  belocs-locales-bin                         2.4-2.2ubuntu5                       tools for compiling locale data files
ii  boo                                        0.7.6.2237-6                         a python-like language and compiler for the 
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1         OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  g++                                        4:4.1.2-9ubuntu2                     The GNU C++ compiler
ii  g++-4.1                                    4.1.2-16ubuntu2                      The GNU C++ compiler
ii  gcc                                        4:4.1.2-9ubuntu2                     The GNU C compiler
ii  gcc-4.1                                    4.1.2-16ubuntu2                      The GNU C compiler
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  mono-jit                                   1.2.4-6ubuntu6                       fast CLI JIT/AOT compiler for Mono
ii  mono-mcs                                   1.2.4-6ubuntu6                       Mono C# compiler
ii  pkg-config                                 0.22-1                               manage compile and link flags for libraries
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
ikkefc3@compaqcaspi8000:~$ 


```

---

### Post by Rupertronco on 2007-10-17
Are you going to answer any of my other questions?

---

### Post by Depressed Man on 2007-10-18
Well earlier there was a post showing 30+ Windows in scale view, and the author of the post noted there was a frame drop as he kept opening more (it dropped from 100 FPS to 30 FPS with that many open I think).

No doubt 165 would cause the graphics with compiz to glitch out.

---

### Post by Forlong on 2007-10-18
> **ikkefc3 said:**
> The task that needs 165+ windows: remembering yourself why you bought an Intel C2D processor (and prooving that PC's are faster than macs for the same money).
I have to disappoint you there.
Compiz is a window manager and what makes it different from most other WMs is the fact that it uses your graphics card.
Most of the time Compiz shouldn't use your CPU at all.

I don't know if it's an issue with the graphics card, with the driver or with Compiz but it has certainly nothing to do with your core duo.

I'm not going to test it myself (mostly because I don't care and... I don't even have 50 divx movies on my harddrive) but maybe others will and you can find the root to that problem.
It's just that you will have troubles convincing people, that it is a problem in the first place, of course..

---

### Post by mannheim on 2007-10-18
There's a bug in launchpad related to this, [here.]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/139669") If you try and open 200 dialog windows with metacity as your window manager, then you will eventually get errors from xlib saying "too many clients", but nothing really bad happens. If you use compiz, then you get the same xlib warnings, but in addition the whole of X eventually crashes and you get returned to the login prompt (as the OP says).

---

### Post by RevolutionMaster on 2007-10-18
> **Lozz said:**
> I should think you'd be hard pushed to find any window manager that would survive that. Like all the others I will have to ask, out of curiosity, what is it that one does with 165 windows?
I know Windows crashes at 150 windows.

---

### Post by mannheim on 2007-10-18
> **RevolutionMaster said:**
> I know Windows crashes at 150 windows.

Well, Windows XP gets to 200 in this screenshot, with no trouble (see attachment). Explorer crashed at around 221!

---

