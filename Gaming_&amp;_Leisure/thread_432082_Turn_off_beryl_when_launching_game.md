---
title: "Turn off beryl when launching game"
date: 2007-05-03
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2007-05-03
I know this appeared on a thread here earlier, but I cant seem to find it anywhere.

I want to "suspend" beryl when I launch a game.  How can I write a script to do this?  I know kwin --replace will work to start it, but how do I get it to return to emerald when I exit the game?

---

### Post by NeoChaosX on 2007-05-03
You have beryl-manager installed and running? The tray icon it provides has some options that allow you to swtich window managers for instances like these.

---

### Post by Naegling23 on 2007-05-03
I have beryl-manager up and running, I can manually toggle beryl on and off.

what I was looking for was a script that would replace beryl with kwin, launch the application, and replace kwin with beryl when I exit the application.  I know I saw such a script floating around somewhere, but I can no longer find it.

---

### Post by hikaricore on 2007-05-04
> **Naegling23 said:**
> I have beryl-manager up and running, I can manually toggle beryl on and off.

what I was looking for was a script that would replace beryl with kwin, launch the application, and replace kwin with beryl when I exit the application.  I know I saw such a script floating around somewhere, but I can no longer find it.

If you can't find it, it's not too hard to throw something together yourself:

```

#! /bin/bash

kwin --replace &
# launches kwin to replace beryl
sleep 2
# obvious pause to allow kwin a few seconds
/usr/bin/applicationyouwanttorun &&
# application params and location here will hold script until exit
sleep 2
# another obvious pause so beryl isn't launching the exact second you close the game
beryl --replace &
# launch bery to replace kwin after game exit

```

It's not perfect, but it should give you an idea of one possible solution.

---

### Post by Eazy© on 2007-05-04
You find one script in my tips/hint for ut2004
[http://ubuntuforums.org/showthread.php?t=374469](http://ubuntuforums.org/showthread.php?t=374469)

```
#!/bin/bash

killall -s USR2 beryl-manager
ut2004 $@ ;
killall -s USR2 beryl-manager
beryl & emerald --replace & 
exit 0
```

---

### Post by Naegling23 on 2007-05-04
Thanks, those were exactly what I was looking for, Im going to try hikaricore's script when I get home.  

Its not difficult to disable beryl when launching a game, but since im not the only one who uses my computer, I have to "idiot proof" it.

---

### Post by Naegling23 on 2007-05-21
this worked great....for a while.

I was playing around with my monitor settings, and lost the ability to use kwin --replace, it errors, and the game wont launch.  I tried an older xorg.conf, reinstall of kwin, logging in as a different user...nothing.  I can still toggle using bery-manager, but just not the terminal.  For the past 3 days, I have tried this forum, google, and irc, but no one has even tried to offer a suggestion yet alone figure out what the problem might be.

---

### Post by Eazy© on 2007-05-22
Did you try my script? I never got the "kwin --replace &"-method to work.

---

### Post by Naegling23 on 2007-05-22
actually easy, your script has never worked for me.

I fixed the problem, but I'm not sure what I did.  I played around with so many things.  The last thing I remember trying was sudo killall beryl-manager.  I got a message saying something to the effect of beryl-manager(####) could not be killed.  So I tried sudo kill ####.  This knocked out my window boarders, and I couldnt get them back, so I logged out, and back in, and everything worked!!!  Im not sure exactly what the problem was, or how I fixed it, but it must have been a hidden beryl-manager that was not showing up in my processes menu, so I couldnt kill it.  The killall must have found it.  Oh well, everything is back to normal, and thats what matters.

---

