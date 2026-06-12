---
title: "Blank desktop after updating after fresh install on AAO 9.04"
date: 2009-06-17
forum: General Help
---

### Post by Banny706 on 2009-06-17
After a fresh install, I switch to normal desktop, check all the repositories then do my first update.  Upon rebooting, which is required after the first update, I get the cursor on a blank desktop where I have only the wallpaper and right-click menu on the cursor.  No panels, no icons.  Any ideas?  Due to this problem I installed regular Ubuntu on AAO.

---

### Post by earwick84 on 2009-06-20
I'm having the same problem.

---

### Post by ganeshIyer on 2009-10-12
Same here...

---

### Post by TerrorFox on 2009-10-15
I had a similar problem, running on an AAO with NBR. It turned out to be a problem with compiz, it doesnt work right with NBR so just don't install compiz and you wont have any problems. Im not sure if there is anything else you can do.

---

### Post by Dusto on 2009-10-26
has anyone else come up with a solution to this problem? COMPIZ didn't work for me as I removed it and restarted my AAO ZG5. I still have a blank desktop with NOTHING, literally nothing, on it. I'm also having problems with WIFI connections. I am totally new to Ubuntu. I have it on my PC at home and it works great. Some little hitches, but nothing a google search couldn't fix.

Not having WIFI is kinda a big deal, and a blank desktop is a big deal. I need some serious help here as I am having real issues trying to find solutions to these problems on my own.

thanks in advance.

Dusto

---

### Post by dbyjazz on 2009-10-26
I think your guy's screen resolution's are messed up. Mine does that too on a fresh install.

open terminal. I believe it's (Ctrl + Alt + F1)sorry I'm on my windows machine lol. and type this in:

```
gksudo gedit /etc/X11/xorg.conf
```

Add a block like this to the "Screen" section:

```
Subsection "Display"
    Depth 24
    Modes "1280x768"
    Virtual 1280 768
EndSubsection
```

but change 1280x768 to your screen preferences

hope that helps

edit: I would change it to a fairly low resolution so you know that you're seeing everything..

---

### Post by Dusto on 2009-11-03
> **dbyjazz said:**
> I think your guy's screen resolution's are messed up. Mine does that too on a fresh install.

open terminal. I believe it's (Ctrl + Alt + F1)sorry I'm on my windows machine lol. and type this in:

```
gksudo gedit /etc/X11/xorg.conf
```Add a block like this to the "Screen" section:

```
Subsection "Display"
    Depth 24
    Modes "1280x768"
    Virtual 1280 768
EndSubsection
```but change 1280x768 to your screen preferences

hope that helps

edit: I would change it to a fairly low resolution so you know that you're seeing everything..

I hate to be an ***, but unless you have actually encountered the problem you'd know that it wasn't a display issue. Thanks for trying. To run any command I have to use "Alt-F1" to bring up a drop down list of all available options. I can't change the desktop background, I can't easily navigate through the program without having to hit "ALT-F1" every single time. It's not a display issue and, to the best of my knowledge, has yet to be resolved. It's getting a bit unnerving. I also STILL can't wirelessly connect to my home network. Why is it sooo hard to find answers to these seemingly common questions?!

---

### Post by Banny706 on 2009-11-08
I marked this solved as I upgraded to 9.10

Thanks for the posts.

---

### Post by dbyjazz on 2009-11-09
> **Dusto said:**
> I hate to be an ***, but unless you have actually encountered the problem you'd know that it wasn't a display issue. Thanks for trying. To run any command I have to use "Alt-F1" to bring up a drop down list of all available options. I can't change the desktop background, I can't easily navigate through the program without having to hit "ALT-F1" every single time. It's not a display issue and, to the best of my knowledge, has yet to be resolved. It's getting a bit unnerving. I also STILL can't wirelessly connect to my home network. Why is it sooo hard to find answers to these seemingly common questions?!

hey don't flip out apparently you don't know what you're doing if you can't fix such a simple problem. I thought what might be going on is that you can't see the panels because you're screen resolution is messed up, as in you're only seeing the center of your screen.

Don't flip out on people when they're only trying to help.

and sorry I didn't know it was a rule all of a sudden that you could only help people out if you've had the problem yourself :roll:

---

