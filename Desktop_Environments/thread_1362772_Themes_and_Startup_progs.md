---
title: "Themes and Startup progs"
date: 2009-12-23
forum: Desktop Environments
---

### Post by egravede on 2009-12-23
So I installed a new theme and thought it would be cool if I could have my email, a terminal, pidgin, and my web browser load up on startup.  Everything I read said to go to Sessions, but I can't seem to find that.  Instead I just went to start up programs and set what I wanted.  Now though there are two black bars that are attatched to NOTHING, no X to close or maximize or minimize, nothing.  When I alt+tab through open windows it shows them as the correct program, but they are just frozen.  I can open other instances of the respective programs as well.

If needed I can provide a screenshot.  I just want to get rid of those black bars.

---

### Post by quixote on 2009-12-24
Do the black bars go away if you remove those programs from Startup Apps?  Or are you stuck with them regardless?  Either way, I'm not sure what to suggest, but I suspect it'll be harder to fix if they're there regardless of the Startup situation. :(

(Also, in this sentence, *I can open other instances of the respective programs as well*. did you mean "can't"?  I ask because the "as well" kind of implies it should be the same situation. ??)

---

### Post by egravede on 2009-12-28
No the black bars stay there.  I've managed to get rid of two of them (which were a terminal and pidign) but the evolution black bar is still stuck at the top of the screen.  

Hmm with that sentence...for example if I Alt+Tab it'll show Evolution (the black bar) but I can still OPEN(click on icon) Evolution and it will come up, but the black bar will still be there...

Does that make sense?  (I've removed everything from start up progs and I still have this issue)

---

### Post by quixote on 2009-12-29
One thing to try is to post your question on the theme's page at gnome-look, or wherever you found it.  Which theme is it by the way?  (Then I'll know not to try it :D) Does the problem go away if you switch back to your previous theme?

---

### Post by egravede on 2010-01-05
hahaha its a mix between avalon and a few other ones.  I dont think its the theme in itself, I think it has to do something with compiz and how i set the start up programs...  i just ended up hiding the bars with other bars over it hahaha

ill post a screenie to show :D

[IMG]http://img46.imageshack.us/img46/351/screenshotue.png[/IMG]

see the bars with no title?  one is a terminal and the other is evolution lol...

---

### Post by egravede on 2010-01-05
wow i just saw my post...
sorry about that haha

---

### Post by macjinlan on 2010-01-05
Hi, egravede. How i can make this menus on destkop like you'r screenshoot? :P

---

### Post by quixote on 2010-01-06
I can see why those black bars bother the hell out of you.  It's a gorgeous desktop!  Bad black bars have no place in something like that.  I second macjinlan: can you tell us exactly how you did that?  Including the anti-black bars kludge?  (Sometimes a kludge is the shortest distance between two points :D.)

---

### Post by egravede on 2010-01-07
its a mix between avalon and enduroblack(themes i found on gnome-look)
just have to install emerald and compiz(which there are extensive threads about here)

the background i found after googling for a while, if you'd like i can host it somewhere and give a link

the menu bars are a subset of the avalon windows

as for the kludge...i just put the corresponding bar over it haha
ex. the top black bar WAS evolution(its not running, the bar is just stuck) so i opened another instance of it and placed the window over it

same with the other one(it was a terminal window) :D

---

### Post by quixote on 2010-01-07
Cool!  Thanks!

---

### Post by stinkeye on 2010-01-07
> **egravede said:**
> So I installed a new theme and thought it would be cool if I could have my email, a terminal, pidgin, and my web browser load up on startup.  Everything I read said to go to Sessions, but I can't seem to find that.  Instead I just went to start up programs and set what I wanted.  Now though there are two black bars that are attatched to NOTHING, no X to close or maximize or minimize, nothing.  When I alt+tab through open windows it shows them as the correct program, but they are just frozen.  I can open other instances of the respective programs as well.

If needed I can provide a screenshot.  I just want to get rid of those black bars.
If your using compiz try this script which will start the programs you want after compiz is loaded.
It's really only needed for the ones which draw a window to your desktop on startup.
**[COLOR="Red"]The Dbus plugin in ccsm > utility must be enabled.[/COLOR]**
```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ $(dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/dbus/screen0 org.freedesktop.compiz.list | wc -l) != 0 ]
	then
		DISPLAY=:0.0 [COLOR="Magenta"]gnome-terminal[/COLOR] >/dev/null 2>&1 &
                DISPLAY=:0.0 [COLOR="#ff00ff"]opera[/COLOR] >/dev/null 2>&1 &
               
                
		done="true";
	else
		echo "WAITING"
		done="false"
		sleep 5;
	fi
done
exit 0
```
[COLOR="#ff00ff"]Change to programs you want.[/COLOR]
Save as startdelay and make executable by right clicking... properties > permissions.
Then create a link to startdelay in system > preferences > startup applications.

---

