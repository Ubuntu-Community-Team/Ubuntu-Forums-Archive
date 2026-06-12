---
title: "noob problem with compiz!"
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by generollins on 2008-04-12
Hi

I'm a complete noob with Linux. Had some experience using Mandriva and Fedora and isntalled gOS which is basically Ubuntu 7.10

I don't understand all these terms etc compiz, emerald. I followed a video on youtube last night on how to get the cube working and certain effects on the desktop.

At the moment i have my ATI Radeo Xpress 1100 driver installed and I can open CCSM and emerald only they don't seem to do anything. When i go to visual effects i noticed that the "None" is selected. But when I try and select the other options the screen kind of flickers and does something and then it looks like its loading then i get "DESKTOP EFFECTS COULD NOT BE ENABLED"

Any ideas what is missing? I have looked around on this forum but nothing seems to be working.

When typing compiz in terminal i get



ian@ian-gOS:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

---

### Post by Half-Left on 2008-04-12
Try emerald --replace in the console. I suspect that your using Xgl because it supports your cards better?, did you install Xgl yourself?

---

### Post by generollins on 2008-04-12
I think so!! I followed this video

[http://www.youtube.com/watch?v=TS--y0XXO7o]("http://www.youtube.com/watch?v=TS--y0XXO7o")

---

### Post by russo.mic on 2008-04-12
try compiz --replace

compiz won't by default kill metacity.

Russo

---

### Post by Zorael on 2008-04-12
Don't you need to start compiz with the --replace argument as well? Or did they change this?
```
$ compiz --replace &
```



As for terms. Please correct me if I'm wrong someplace; I'm still fairly green. "Window manager" might be a misnomer, for one.


Compiz is a window compositioner.
> **Wikipedia][Window compostioners allow] for advanced visual effects, such as total (or in some cases, partial) transparency, and/or fading in and out, of application windows, system panels, and the like, as well as the potential addition of simulated three-dimensional shadows beneath windows, complex animation of window resizing, reshaping and movement, to name just a few possible features.[/quote]
It also has window management features, such as keeping track of what window has focus, switching between them, moving them, etc.
[quote=Wikipedia]A window manager is computer software that controls the placement and appearance of windows within a windowing system in a graphical user interface said:**
> 
Emerald is a window decorator that handle how windows "look". Basically; titlebars, borders. There are others, some even included in the compiz package (gtk-window-decorator, kde-window-decorator), with which people have had varying success. (I'd go as far as to call kde-window-decorator broken as heck. :> )
[quote=Wikipedia]Window decorations are provided by windowing systems to improve the usability of a multi-windowed desktop. They typically consist of a title bar along the top of each window and a minimal border around the other three sides, although this can often be varied upon if the user wishes.

In the predominant layout for modern window decorations, the top bar contains a title and buttons which perform windowing-related actions such as closing or minimising. The border exists primarily to allow the user to resize the window.

Window decorations are important in developing the look and feel of a desktop environment. However, modern systems allow for great customization of the colors, styles and animation effects used. User modifications some times cross between the appearance of different desktop environments.


Compiz by itself does not draw menu bars onto windows, and as such, unless you have Emerald (or some other window decorators; again, such as gtk-window-decorator and kde-window-decorator), you *WILL* end up with borderless and titlebarless windows. Obviously, this can also happen due to other reasons, and this is just one of them.

"Normal" window managers, such as Gnome's Metacity and KDE's KWin, are window managers in their own right with some barebone window compositioning features. They are also window decorators, so you don't need a third-party decorator to get titlebars. Furthermore, this means that they each get their own look; windows in Gnome look Gnome-y, windows in KDE look KDE-y. Whereas if you're running Emerald, you can use the same themes regardless of if you're running Gnome or KDE or Xfce or whatnot, since it's still the same Emerald. Hence the occasional "I ran Compiz and suddenly my windows have red titlebars" threads, which is an effect of Emerald taking control and applying its own default theme.

Emerald can not run as a complete window manager, since it does not handle what windows have focus and such tasks. Furthermore, it needs a window compositioner to be able to draw its themes, so you can't use Emerald without Compiz (or equavilent). Much like you can't use Compiz without Emerald (or equavilent).

So!
[list][*]You need a window manager and a window decorator to be able to work with windows. Window compositioners are optional. Eyecandy.
[*]Compositioners without decorators means no titlebars nor borders.
[*]Decorators that need compositioners (i.e Emerald), if invoked without one running, means no titlebars nor borders.


[*]Metacity (Gnome default) is a window manager and a window decorator. (Not sure about compositioning features.)
[*]KWin (KDE default) is a window manager, a window decorator and a limited window compositioner.
[*]Compiz is a window compositioner and a window manager.
[*]Emerald is a window decorator.
[*]Beryl is the old compositioner which was to begin with a branch off of Compiz. It has now been succeeded by Compiz, so it's deprecated.[/list]
So since you need at least a window manager and a window decorator, you need to supplement one with another if you want to use Compiz or Emerald.

---

### Post by generollins on 2008-04-14
right ok, so what would you recomend me install to compliment these? and how do i go about installing it?

---

### Post by Zorael on 2008-04-15
You should be fine with what you have, compiz and emerald.

Perhaps killing metacity first and then starting compiz would work?
```
$ killall metacity && compiz --replace
```

---

### Post by generollins on 2008-04-18
ok tried that and just get the following


ian@ian-gOS:~$ killall metacity && compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

---

