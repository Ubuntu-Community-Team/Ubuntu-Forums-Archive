---
title: "How can I open UT2004 in a window?"
date: 2005-09-17
forum: Gaming &amp; Leisure
---

### Post by linkunderscore on 2005-09-17
I want to play it in a window so that I can still see other things like gaim, xchat, etc. I know I can press alt-enter and put the game into a small window but it messes up the mouse and I can't click out of the UT2004 window. 

Is there a terminal command that will open it in a window?

---

### Post by Drakx on 2005-09-17
[QUOTE=linkunderscore]I want to play it in a window so that I can still see other things like gaim, xchat, etc. I know I can press alt-enter and put the game into a small window but it messes up the mouse and I can't click out of the UT2004 window. 

Is there a terminal command that will open it in a window?[/QUOTE]
 have your tryed going into options and telling it to run in window instead of full screen ?

---

### Post by linkunderscore on 2005-09-17
yea but it doesn't save that setting. when i restart it the next time it starts fullscreen.


EDIT: it keeps it fullscreen but it won't allow me to alt-tab over to other windows when the game is running. Is this fix-able or is this just a linux thing.

---

### Post by professor_chaos on 2005-09-18
You could try modifying ~/.ut2004/System/UT2004.ini
Theres a line StartupFullscreen=True.
You could try changing it to False and see if it changes back. If it does, you could try removing the write permissions of the file. 

Just a shot in the dark, no sure what will happen.

---

### Post by linkunderscore on 2005-09-19
[QUOTE=professor_chaos]You could try modifying ~/.ut2004/System/UT2004.ini
Theres a line StartupFullscreen=True.
You could try changing it to False and see if it changes back. If it does, you could try removing the write permissions of the file. 

Just a shot in the dark, no sure what will happen.[/QUOTE]


well i can get it to start in a window, but I can't switch to other windows. I want to be able to "alt-tab" to gaim or xchat(i know ut has irc built in but whatever). 

Is there a way to switch to another window?

---

### Post by Curlydave on 2005-09-19
I'm not sure about this, sorry I can't help.

What I want is a way to let it run in fullscreen mode, but be able to minimize and switch to other windows when I want, like in Windows. I put in this request on the Breezy forum several times, but with no responses.

---

### Post by jdodson on 2005-09-19
[QUOTE=Curlydave]I'm not sure about this, sorry I can't help.

What I want is a way to let it run in fullscreen mode, but be able to minimize and switch to other windows when I want, like in Windows. I put in this request on the Breezy forum several times, but with no responses.[/QUOTE]

Yeah to my understanding this is not a option they are going to add.  I think this is a Gnome desktop issue, not a Ubuntu issue perse.  

It is a nice feature in Windows.  I would suggest attempting to live without it.  There is, however the ALT+F? option.  So you can go to a terminal, use lynx to surf the web, or whatever.  Not really that great, but you get something at least.

---

### Post by linkunderscore on 2005-09-20
[QUOTE=jdodson]Yeah to my understanding this is not a option they are going to add.  I think this is a Gnome desktop issue, not a Ubuntu issue perse.  

It is a nice feature in Windows.  I would suggest attempting to live without it.  There is, however the ALT+F? option.  So you can go to a terminal, use lynx to surf the web, or whatever.  Not really that great, but you get something at least.[/QUOTE]


I figured its a windows manager issue. I am currently running enlightened gnome. Do you know if any of the other wm's allow this kind of fast-window-switching?

---

