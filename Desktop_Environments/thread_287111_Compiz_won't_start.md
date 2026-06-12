---
title: "Compiz won't start"
date: 2006-10-28
forum: Desktop Environments
---

### Post by bdragonmsl on 2006-10-28
I've installed the packages in synaptic for compiz, and have gotten my xgl and glx running, but now compiz won't start.  I've also tried using the replace function and I then get windows without decorations like no titlebars, yet can use compiz functions.  Below is what happens when I try to start compiz.  Any help would be greatly appreciated.
> 
bdragonmsl@bdragonmsl-desktop:~$ compiz - start
bdragonmsl@bdragonmsl-desktop:~$ compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz.real: No manageable screens found on display :0.0

---

### Post by John.Michael.Kane on 2006-10-28
Here the guide i used [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

Or if you want to use aiglx

[http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

---

### Post by bdragonmsl on 2006-10-28
It seems that that wiki is for beryl only.  I'm trying to use compiz.  Thank you though.

---

### Post by gruffy-06 on 2006-10-28
That is, *compiz-start*, without any spaces.

---

### Post by gruffy-06 on 2006-10-28
If you can't use *compiz-start*, then you may have a different version installed.

If you are using *compiz --replace*, don't forget to specify plugins after the --replace option. Examples are: resize, place, move, wobbly, water. Use *gconf-editor* to view all installed plugins.

After that, run *gnome-window-decorator* or *cgwd*, depending on which window decorator you wish to use.

---

### Post by John.Michael.Kane on 2006-10-28
bdragonmsl the wiki guide linked to works fine. I  used it,and had the option for compiz or beryl listed in the beryl manager.

---

### Post by bdragonmsl on 2006-10-29
I installed it through synaptic, and all of it's dependencies.  The version that I'm trying to use is 0.0.13.38-0ubuntu3.

---

