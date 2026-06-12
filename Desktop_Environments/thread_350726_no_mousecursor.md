---
title: "no mouse/cursor"
date: 2007-02-01
forum: Desktop Environments
---

### Post by nox.freak on 2007-02-01
Just installed ubuntu 6.10 and under Gnome I don't have a cursor. its there but I can't see it. I installed kubuntu-desktop to see if the cursor would show up in the GUI but no luck.



Hardware:
NVidia 6600 128MB
AMD64 3200
1GB RAM

---

### Post by nox.freak on 2007-02-03
Found the fix you have to add the fallowing line to you xorg.conf under the "Device" section
Option "HWCursor" "off"

---

### Post by Tasogare_Mike on 2007-02-03
Thank you, I had the same problem...err... HAVE the same problem. I hope I can figure out how to use what you just typed because I'm lost when it comes to linux.

---

### Post by Tasogare_Mike on 2007-02-03
Actually, ...yeah I give up. Especially with the live cd. 

Can someone walk me through this please so that I can live boot with a cursor? Please please please please please. I'll give you a copy of Ubuntu for free. :guitar: 

I love Ubuntu! :)

---

### Post by Tasogare_Mike on 2007-02-04
Ok I figured out how to do this but my G-card is not being recognized. I think that is why I can't apply the aforementioned solution.

I have a evga 7600gs. Is it my driver that I have installed in windows that is affecting my linux? Is that possible? Other than that, is there a way I can force my GPU to be recognized in the live version?

Sorry but I'm not very familiar w/ live versions of anything. Thank you.

---

### Post by gradedcheese on 2007-02-04
> **Tasogare_Mike said:**
> Thank you, I had the same problem...err... HAVE the same problem. I hope I can figure out how to use what you just typed because I'm lost when it comes to linux.

If you don't have a cursor and need to edit some files (to set the hwcursor option in this case), you should know that you can switch between one or more text shells and graphical shells as needed.  It works like this:

Control+Alt+F1 through Control+Alt+F6 are text shells
Control+Alt+F7 and up are graphical shells (you can use Control+Alt+F7 to get back to the default one you're in now)

I guess my suggestion is: switch to a text shell, open the file /etc/X11/xorg.conf in a text editor, and then make the edit suggested by "nox.freak".  Save the file and leave the editor and now two X again, either by opening another graphical shell (ex: Control+Alt+F8 ) or going to the F7 one and killing it (Control+Alt+Backspace).  You could also just type 'startx' in a text shell to fire up the GUI.

I'm not sure which text editor you'd prefer but it looks like 'pico' is installed by default and that seems to be one that people new to the shell like to use.  So, to edit the file in question you would run:

sudo pico /etc/X11/xorg.conf

and scroll to the 'Device' section and then type in the relevant option.

---

### Post by gejr on 2007-03-08
I'm sorry to revive this thread, but I'm having this problem and I cant figure out how to do this. I've tried with Option "HWCursor" "off" in every section I find reasonable now, and still no mousecursor...what can cause this annoying problem?!:D

---

### Post by Tasogare_Mike on 2007-04-20
Well Hallellulja (or however you spell it)...

Feisty Fawn live boots with no such problem. I'm assuming that thereis a driver for my 7600GS graphics card that was included for the Fawn.

Thanks for the help though.

---

