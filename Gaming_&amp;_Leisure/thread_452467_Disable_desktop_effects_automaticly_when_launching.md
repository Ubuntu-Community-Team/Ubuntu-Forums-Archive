---
title: "Disable desktop effects automaticly when launching a game?"
date: 2007-05-23
forum: Gaming &amp; Leisure
---

### Post by BoneyOne on 2007-05-23
Ok I've been playing GuildWars, City of Heroes, HL2DM, and CS:S using wine.
Things are great, but unless I run the games windowed (which I don't care to do) I have to disable the desktop effects before launching the games.

Is there a way to create a shell script that will disable the desktop effects, launch the game, and maybe even re-enable the desktop effects upon me exiting the game?

Sorry if this has been covered before I found nothing with the search. Also I'm new to Linux and shell scripts (plenty of experience with DOS batch files) so take it easy on me. ;)

Thanks

---

### Post by blazercist on 2007-05-23
use Xnest my son.

sudo apt-get install Xnest

then you can run the games inside of Xnest

Use Xnest. Once you have installed Xnest, you should be able to 

Xnest -display :1; env DISPLAY=:1 wine name_of_application 

If that doesn't work, try 

Xnest -display :1 -depth 8; env DISPLAY=:1 wine name_of_application 

If you have more than one display, or are using :1 for something already (e.g. vnc or another Xnest session), simply use :n, where n is any unused display number, in place of :1. 


Use display :0  that works for me.

---

### Post by BoneyOne on 2007-05-23
Never heard of Xnest, but after looking at it...thanks

Only one thing when I try it fails. Gives me an error stating *"Application tried to create a window, but no driver could be loaded."*

Did a search but couldn't find any info that was of use for me.

---

### Post by blazercist on 2007-05-23
honestly you've stumped me there, you'll need an Xnest guru for that... it just works for me, try a different display?

---

### Post by Cappy on 2007-05-23
[http://ubuntuforums.org/showthread.php?t=374469](http://ubuntuforums.org/showthread.php?t=374469)

In this thread there is a script you can use (look for **Beryl and UT2004**). You will need to create a new script for each game, however. I don't know enough about linux scripting to modify that so you can just use something like "stopberylfor gamenamegoeshere". Now I'm curious ...

---

### Post by Naegling23 on 2007-05-23
[http://ubuntuforums.org/showthread.php?t=432082](http://ubuntuforums.org/showthread.php?t=432082)

follow that thread.  I recommend Hikaricore's option, it worked great for me.

I put the custom launcher in the same folder as the .exe, and point my shortcut to the .sh file.

---

### Post by aidanr on 2007-05-23
i usually do something like

#!/bin/bash
killall beryl &&
cd /path/to/game/folder &&
./game &&
beryl &

should be the same with desktop effects, just replace beryl with compiz

---

### Post by Sutur on 2007-10-28
I reckon the best idea is to:

[LIST=1]
[*]Log out.
[*]Select session 'Failsafe Terminal'.
[*]Log in.
[*]Start your game.
[/LIST]

Simple, effective and requires no work at all. Also, you'll have no junk running, which should probably increase your FPS significantly.

---

### Post by Viverrid on 2007-10-29
I saw this the other day and it might be what you're looking for:

[http://ubuntuforums.org/showthread.php?t=533257](http://ubuntuforums.org/showthread.php?t=533257)

-Viverrid

---

### Post by Crafty Kisses on 2007-10-29
> **aidanr said:**
> i usually do something like

#!/bin/bash
killall beryl &&
cd /path/to/game/folder &&
./game &&
beryl &

should be the same with desktop effects, just replace beryl with compiz

Same here.

---

