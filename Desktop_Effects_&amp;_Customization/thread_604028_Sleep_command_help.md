---
title: "Sleep command help"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by tadada on 2007-11-05
Ok I wanted a terminal on my desktop like you see in the pictures with devil's pie but it never worked out. anyways I stumbled literally onto a tutorial on how to do this with only compiz-fusion so I go trough it and IT WORKS. But then next day at start up the terminal is in the wrong place. It is supposed to be in the center not the top left corner. I narrowed it down to the startup order of it starting before Compiz so Compiz can't place it in the center. I think well all I have to add it "sleep 10 &&" before the command but nothing works I even tried putting it in a script that is run. NOPE. can anyone help me?

I run Gutsy customized Compiz effects (kinda duh since I hadda fiddle with em to get the effects.) If I run the command from a terminal prompt it works (even if I add the sleep part it still gives the terminal on my desktop.)

here is the command:
gnome-terminal --window-with-profile=trans

the script:
#!/bin/bash
#
# gnome-terminal with profile trans
sleep 10 && gnome-terminal --window-with-profile=trans

EDIT: Mabye I shoulda given it a better title,,,

---

### Post by kast on 2007-11-05
a little confused, could you better explain? Is one of those command starting up compiz-fusion?
if not how do you know how long to sleep?

---

### Post by tadada on 2007-11-05
All the command does is starts terminal with the profile called trans now the title of the window will be trans and Compiz is set to make it have no window border or anything because that is it's name but at startup compiz starts after the terminal so it can't tell the terminal where to go. But the sleep command I put in to slow the terminal startup down isn't working and instead makes nothing happen.

The setup is so that the profile has black text no scroll bar no menu bar then compiz is told to rid the terminal (that his the name trans because profile trans is being used) of it's window border and to make it non movable non resizable and to always start it in the center and have set at the size I said. If you need I'll get a picture in how it should run and how it does after startup and post them.

---

### Post by tadada on 2007-11-06
I don't suppose anyone has any help on this

---

### Post by kast on 2007-11-06
How about instead of trying to make it wait until Compiz,  we try and just restart it after compiz? 

Sorry i don't use Compiz-Fusion so trying to figure out exactly what your trying to do is hard.

---

### Post by Zorael on 2007-11-06
Well, there are several ways to deal with this.

```
#!/bin/bash

compiz *<your arguments of choice>* &
sleep 5
gnome-terminal --window-with-profile=trans &
```

Wouldn't that work? If you use that script to launch them both, you *know* gnome-terminal will be evoked 5 seconds after compiz was called.


The more advanced way would be:
```
#!/bin/bash

while true; do
	if ps -C compiz.real > /dev/null
	then
		# running, sleep to be sure it's loaded and then evoke terminal
		sleep 2
		gnome-terminal --window-with-profile=trans &
		break
	else
		# not running, sleep and let while-loop cycle
		sleep 1
	fi
done
```

That *should* do the trick. There's probably some smarter way to do it, but that's beyond me. And the sleep values might need tinkering with.

---

### Post by Zorael on 2007-11-06
```
if [ "$(pidof compiz.real)" ]
```
...might also work.

---

