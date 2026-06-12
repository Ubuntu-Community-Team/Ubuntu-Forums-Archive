---
title: "how to disable compiz for wine"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by donkyhotay on 2007-11-07
I use compiz for general use however it does conflict with my 3D wine games and I need to turn it off temporarily for that. Disabling compiz manually is a bit of a pain so I wrote a series of short scripts for my most common wine games that to toggle that basically goes: 

metacity --replace &
wine /name/of/file
compiz --replace &

which works perfectly when run in a terminal. When I attempt to run these scripts from the main gnome menu though it simply attempts to run the wine program without disabling compiz first. Does anyone know why this is and what (if anything) I can do to fix it?

---

### Post by kshane on 2007-11-07
> **donkyhotay said:**
> I use compiz for general use however it does conflict with my 3D wine games and I need to turn it off temporarily for that. Disabling compiz manually is a bit of a pain so I wrote a series of short scripts for my most common wine games that to toggle that basically goes: 

metacity --replace &
wine /name/of/file
compiz --replace &

which works perfectly when run in a terminal. When I attempt to run these scripts from the main gnome menu though it simply attempts to run the wine program without disabling compiz first. Does anyone know why this is and what (if anything) I can do to fix it?

I believe if you use two ampersands instead of one, you'll get the desired result.

Kevin

---

### Post by donkyhotay on 2007-11-08
I tried that but there was no change.

---

### Post by nickelby on 2007-11-09
Perhaps you would like to try something easier which is to install "fusion-icon" which will enable/disable compiz just by using the mouse. I find it works quite well for me whenever I want to disable compiz. Plus it has the advantage of using other options with compiz.

On your scripting issue, perhaps you need to add in a "wait time" for each of the statements. I am not sure but that's just an idea.

---

### Post by tumbl3r on 2008-02-03
Did you start your script with #!/bin/bash so it knows to use the bash interpreter.

---

### Post by clonek on 2008-02-03
If you're running your games in full screen mode, you don't need to disable compiz. 

System > Preferences > Advanced Desktop Effects Settings

Click Gerneral

Uncheck "Undirect Fullscreen Windows"

Compiz will no longer render fullscreen windows.

---

