---
title: "[SOLVED] Xfce screenshot"
date: 2007-12-12
forum: Desktop Environments
---

### Post by santiagoward2000 on 2007-12-12
Hi there!
I wanted to know, is there any way to set my PrtSc button to take a screenshot in Xfce without having to install **gnome-utils**?
Thanks!

---

### Post by jken146 on 2007-12-12
In Applications > Settings > Keyboard Settings > Shortcuts there is a list of commands and KB shortcuts assigned to them.  I would map PrtSc to the screenshot command but for 2 things: 1) that list is greyed out and 2) I don't know what the command is.

There is always the Screenshot panel item.

---

### Post by santiagoward2000 on 2007-12-12
> **jken146 said:**
> In Applications > Settings > Keyboard Settings > Shortcuts there is a list of commands and KB shortcuts assigned to them.  I would map PrtSc to the screenshot command but for 2 things: 1) that list is greyed out and 2) I don't know what the command is.

There is always the Screenshot panel item.

Thanks for answering. I was asking because I wanted to know if anyone knew what the command was. I searched my system, but the only *screenshot* file I found is GIMP's plugin...
I know I could use the panel item, but I wanted to take a screenshot of my cube, and I can't use during cube rotation.

---

### Post by Tenken on 2007-12-12
Try a command line program called scrot, it's in the repos and can be passed some arguments. For example 
```
scrot -d 5
```
waits for 5 seconds before taking the screen screen shot.

---

### Post by jken146 on 2007-12-12
I think compiz fusion has something for screenshots.  I can't check right now on this comp.  If I am right though, you should be able to map a keystroke to it.

Let me know if you find a way!

---

### Post by jken146 on 2007-12-12
Thanks Tenken.  The only problem left for me is how to edit the kb shortcuts.

---

### Post by santiagoward2000 on 2007-12-12
> **jken146 said:**
> I think compiz fusion has something for screenshots.  I can't check right now on this comp.  If I am right though, you should be able to map a keystroke to it.
Yes, there are 2 ways with Compiz-Fusion. One is setting the command in **General Options**, but then I have the same problem as before. The other is using the **Screenshot** plugin, but you can only set it to work with mouse buttons, not just a key.

> **Tenken said:**
> Try a command line program called scrot, it's in the repos and can be passed some arguments. For example 
```
scrot -d 5
```
waits for 5 seconds before taking the screen screen shot.
Hey, thanks tenken, I'll give it a try! Just a few questions:
[LIST=1]
[*]If I want to use it with no delay I just type ```
scrot
```?
[*]After I use it, does it copy the image somewhere or does it open a window so I can select where to save it (like gnome-screenshot)?
[/LIST]
Thanks!

---

### Post by jken146 on 2007-12-12
From reading the man page, I discovered it saves the screenshot in the directory you're currently in, but this can be changed with options.

---

### Post by Tenken on 2007-12-12
Right giving it no arguments takes the screen shot immediately,and it doesn't ask you where to save it, it just puts it in your home folder.

---

### Post by jken146 on 2007-12-12
OK, I figured out that to change the keyboard shortcut settings all I had to do was create a new "Theme" on the left hand side.  I assigned PrtSc to scrot.

---

### Post by santiagoward2000 on 2007-12-12
THANKS TENKEN!
This did it! I set Compiz to do it. I went to **General Options / Commands** and set *Screenshot command line* to:
```
scrot '%d-%m-%Y-(%H:%M)_$wx$h_scrot.png'
```
so the file's name has the date, time and resolution. Besides, all the files go straight to my home folder :)
Just one more question: Is there any way to set it for the *Window screenshot command line* option? I mean, so it takes a screenshot of the active window only?

---

### Post by Tenken on 2007-12-12
Yep it has an option (-s) that lets you select a specific area, or a window. Hope that helps.

---

### Post by santiagoward2000 on 2007-12-12
> **Tenken said:**
> Yep it has an option (-s) that lets you select a specific area, or a window. Hope that helps.

Thanks, but I was looking for something where I didn't have to use the mouse.

---

### Post by whoscheesemine on 2008-03-05
Does anyone here happen to know though what it is that is used in the GNOME desktop that takes screenshots when you push print screen.

Actually I think I remember hearing somewhere that you could do it in the terminal, something called a screen dump or something? I guess that's what all these screen shot programs use is your computers own "screen dump" what ever that is. Having Xubuntu, I'm trying to keep everything as low key as possible. Does scrot constantly run in my processes? I wish that I could just find somewhere what it is actually that Gnome - Ubuntu uses to take screen shots so that I may be able to take advantage of it, as I'm sure it is probably low key.

---

### Post by santiagoward2000 on 2008-03-05
> **whoscheesemine said:**
> Does anyone here happen to know though what it is that is used in the GNOME desktop that takes screenshots when you push print screen.

Actually I think I remember hearing somewhere that you could do it in the terminal, something called a screen dump or something? I guess that's what all these screen shot programs use is your computers own "screen dump" what ever that is. Having Xubuntu, I'm trying to keep everything as low key as possible. Does scrot constantly run in my processes? I wish that I could just find somewhere what it is actually that Gnome - Ubuntu uses to take screen shots so that I may be able to take advantage of it, as I'm sure it is probably low key.

Hi!
The command Gnome uses is **gnome-screenshot**, and is part od the **gnome-utils** package.
Cheers!

---

