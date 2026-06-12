---
title: "Open in terminal? where is that damn option???"
date: 2006-02-06
forum: Desktop Environments
---

### Post by linuxden on 2006-02-06
Hey,

I have completely forgoten where i saw the option to right click and open in terminal...(its on my desktop but not lappy...)

Quick reminder needed...

Thanks to all.

---

### Post by Praetorian on 2006-02-06
you mean this?
[http://g-scripts.sourceforge.net/cat-executing.php](http://g-scripts.sourceforge.net/cat-executing.php)

---

### Post by engla on 2006-02-06
[QUOTE=Praetorian]you mean this?
[http://g-scripts.sourceforge.net/cat-executing.php](http://g-scripts.sourceforge.net/cat-executing.php)[/QUOTE]
That's a bloated script to do this... all you need is
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal
```

---

### Post by linuxden on 2006-02-06
[QUOTE=engla]That's a bloated script to do this... all you need is
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal
```[/QUOTE]

Engla,

Where would that script be kept, am looking in my ~ directory but cannot find it under nautilus/scripts...

edit: 
praetorian,
Thanks for your response too...

---

### Post by engla on 2006-02-06
You have to put it in ~/.gnome2/nautilus-scripts

Type Ctrl-L in nautilus to be able to enter the location, or make nautilus show invisible files so you can open .gnome2

---

### Post by linuxden on 2006-02-06
[QUOTE=engla]You have to put it in ~/.gnome2/nautilus-scripts

Type Ctrl-L in nautilus to be able to enter the location, or make nautilus show invisible files so you can open .gnome2[/QUOTE]

thanks...

Have this screenshot of my desktop to show you what i wanted... the scrip you gavce me in effect does the same thing but i have to select scripts... 

I just have to right click anywhere and it shows up...

---

### Post by linuxden on 2006-02-06
Ok guys, 

I knew i didnt need scripts but then again i have such bad memory when it comes to what i do to my systems... I should defo keep a log of my tweaks... LMAO

ok there is a program called "nautilus-open-terminal" that does exactly what those scripts do but it incorporates it into the right-click menu... much nicer i think... Anyways its in repositories... check it out...

ps: thanks for all your help!

---

### Post by gooner on 2006-02-08
Thanks, I just reinstalled ubuntu and was trying to remember what that program was called.

---

### Post by linuxden on 2006-02-09
Yeah It puzzled me for a while too... Glad it helped ya out...

---

