---
title: "Making links to programs?"
date: 2009-01-17
forum: General Help
---

### Post by PoopLoops on 2009-01-17
I frequently encounter a situation where I install some program and I have to manually navigate to its folder to run it.  A lot of other programs like gnuplot just let me run it from the terminal by entering "gnuplot".

Is there any way I can do that to other programs that I want?  I know it has something to do with /usr/local/bin, but I'm not sure what and I don't want to kill my computer twice in a day (Win XP keeled over this morning... :P)

---

### Post by Ender41 on 2009-01-17
> **PoopLoops said:**
> I frequently encounter a situation where I install some program and I have to manually navigate to its folder to run it.  A lot of other programs like gnuplot just let me run it from the terminal by entering "gnuplot".

Is there any way I can do that to other programs that I want?  I know it has something to do with /usr/local/bin, but I'm not sure what and I don't want to kill my computer twice in a day (Win XP keeled over this morning... :P)

one way is to go to the /usr/local/bin/ folder and set a symbolic link to your program sudo ln -s /fullpathtoprogram
eg say you have installed realplayer to /opt/real/ for instance
you would cd to /usr/local/bin
and type sudo ln -s /opr/real/realplay

You can also install a custom launcher on your taskbar or just add it to the menu if you want to run it from the gui

---

### Post by PoopLoops on 2009-01-17
That was *exactly* what I was looking for.  Many thanks. :)

---

