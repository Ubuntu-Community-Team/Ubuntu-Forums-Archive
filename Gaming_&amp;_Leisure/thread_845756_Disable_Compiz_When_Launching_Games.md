---
title: "Disable Compiz When Launching Games?"
date: 2008-06-30
forum: Gaming &amp; Leisure
---

### Post by grimdeath on 2008-06-30
Sorry, I read a thread many months ago that stated how to do this but I cannot seem to find it now. Can someone explain how I could disable, and possibly re-enable the full version of compiz when I enter/exit a game.

I have problems with some games when compiz is turned on and have been manually toggling it off for now, just curious if there is a automatic way to make this work.

I am running quake wars from a desktop launcher if that helps.

Thanks!

---

### Post by S1xp4ck on 2008-06-30
I use Compiz Switch which you can obtain [Here](http://forlong.blogage.de/article/pages/Compiz-Switch) .

Basically it throws up a shortcut that will toggle your compiz settings on and off.  Quite handy for us gamers.

---

### Post by grimdeath on 2008-06-30
that works pretty well, now i just gotta remember to hit that button when I enter games :P that should do the trick though.

....now if i could just figure out why my sound works in everything but that game :P

---

### Post by atomkarinca on 2008-07-01
You can write a bash script and make a shortcut. It can be something like this:

```
#!/bin/bash
metacity --replace
wine "~/.wine/drive_c/Program Files/dir/to/the/game/game.exe"
```

But after you quit you should also replace your window manager with compiz again:

```
compiz --replace
```

---

### Post by grimdeath on 2008-07-01
thanks, compiz-switch seems to be doing the trick just fine.

---

### Post by drhabber on 2008-09-11
> **atomkarinca said:**
> You can write a bash script and make a shortcut. It can be something like this:

```
#!/bin/bash
metacity --replace
wine "~/.wine/drive_c/Program Files/dir/to/the/game/game.exe"
```

But after you quit you should also replace your window manager with compiz again:

```
compiz --replace
```

I have found a better solution (finally! :)) and it works like a charm:

> **Twilight in Zero]I just use this script:

```
#!/bin/bash
#  gamerun
#
#  Sun Oct 28 07:17:37 2007
#  Copyright  2007  Enrique Schiel
#  <ecschiel@yahoo.com.ar>

# This program is free software said:**
> ; then
    printf "Disabling advanced desktop efects...\n"
    /usr/bin/metacity --replace &
fi

printf "Running the game...\n"
$@ &
wait $!

if [ $CHANGE == 1 ]; then
    printf "The game is finished. Restoring advanced desktop efects...\n"
    /usr/bin/compiz --replace &
fi

exit 0
```

With this one, I only have to do, for example, to run ZSNES, "gamerun zsnes". Metacity will replace Compiz, the game will run, and after it's done, Compiz will come back. I've already modified all of my opengl game shortcuts with this.

I didn't make this script, but I don't remember where I got it from. The guy's name is up at the top of the script. I just changed its name and added exit 0 to the end.

---

