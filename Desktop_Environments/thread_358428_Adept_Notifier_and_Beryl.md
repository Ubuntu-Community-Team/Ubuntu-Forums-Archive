---
title: "Adept Notifier and Beryl"
date: 2007-02-10
forum: Desktop Environments
---

### Post by djlyx on 2007-02-10
I am having a weird problem with Kubuntu's Adept Notifier and Beryl.  Whenever I use Beryl, the Notifier is always on in the task bar and there is a tiny useless window always open.


Does anyone know how to uninstall or disable Kubuntu's adept notifier?

thanx

---

### Post by barius on 2007-02-12
I'd like to second this bug.  I have the exact same problem on Kubuntu 6.10 w/ Beryl from the repos.

---

### Post by mblinux on 2007-02-13
> **djlyx said:**
> 

Does anyone know how to uninstall or disable Kubuntu's adept notifier?



I believe that you can right click on that small window and select "quit". Then it will ask you if you want the notifier to start automatically next time or not. Then make your choice. If I remember well I resoved this way. Hope this can help you.

---

### Post by mexlinux on 2007-02-13
That always happend to me when beryl is started, then I just open another KDE app that is going to put an icon in th systray (like amarok) and then all those little windows are automatically corrected and sent into the systray....

---

### Post by Kalinda on 2007-02-14
I initially solved this by putting a shortcut to adept in the KDE startup directory and telling it to start after beryl, but I deleted those files  because Beryl was being a pain, so I don't remember the command that goes in the .desktop file.

Regardless, closing it after bootup and reopening it with the command adept_notifier makes it work fine. For me it usually doesn't hide itself in the system tray; the lil green circle thing stays visible even though it shouldn't. Reopening it when beryl is loaded fixes this. Maybe a script should be written to load all system tray apps once beryl is done loading or something.

---

### Post by karmy on 2007-07-06
same problem here and becomes frustrating, please, did anyone found solution for this?

---

### Post by kustodian on 2007-07-31
Same problem with compiz-fusion.

Hope they fix it for Gutsy :)

---

### Post by bmorency on 2007-09-13
I am having the same problem also with compiz fusion. it's a bit of a pain that it takes up taskbar space instead of being in the system tray. i should maybe file a bug over at the compiz fusion or the kubuntu website if there isn't one already.

---

### Post by Zorael on 2007-10-28
Not fixed in Gutsy.

Does anyone know how to write a script that checks if compiz.real is running, and if so, launches adept_notifier?

---

### Post by leftclick on 2007-11-12
I wrote a script for this issue, and some other similar ones.  The script attached goes in "~/.kde/Autostart".  This is what I get from it:

[LIST]
[*]No more annoying "adept_notifier" window
[*]Beryl and Beryl Manager actually start when I log in
[*]No more missing window decorations
[*]No more random failures to start KNetworkManager
[/LIST]

Note that the bit that starts Beryl might be different if you use XGL (I use AIGLX).  It should work with compiz or compiz-fusion, just replace with the relevant command.

One thing I have noticed is that in the Beryl Manager menu, it has KWin selected even though it is definitely Beryl that is running.  Maybe there should be another command or different option to set this correctly?  For me, though, it doesn't matter as I don't need to switch back to flat desktop at all.

See also [this launchpad bug (131013)]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/131013"), it has some other ideas.

If you are getting problems with kicker (the thing with the icons) try looking into dcop (type dcop kicker at command line for a start, and btw it autocompletes under konsole!)

I am very surprised this happens under Gutsy too.  I would think making 3D desktops Just Work(TM) would be a top priority for the Ubuntu guys being a desktop distro.

---

### Post by leftclick on 2007-11-12
> **Zorael said:**
> Not fixed in Gutsy.

Does anyone know how to write a script that checks if compiz.real is running, and if so, launches adept_notifier?

Try this:

```

#!/bin/bash
while [ -z "$( ps -A | grep -e ^.*\\s*compiz.real$ )" ] ; do
  sleep 1
done
echo 'test'

```

This will wait indefinitely, checking once a second, until a "compiz.real" process is running, then echo the word "test".  Just replace the last line with whatever you want to do.

---

### Post by leftclick on 2007-11-12
> **Zorael said:**
> Not fixed in Gutsy.

Does anyone know how to write a script that checks if compiz.real is running, and if so, launches adept_notifier?

Hmm I just re-read the question and my answer and I gave you the right answer to the wrong question lol.  If you just want to check once whether it is running and do something (so if it is not running at that time it does nothing at all), then this is what you want:

```

if [ -n "$( ps -A | grep -e ^.*\\s*compiz.real$ )" ] ; then
  echo 'test'
fi
```

---

### Post by raul_ on 2007-11-12
Just close adept-notifier, tell it to never start automatically, create a little script that says something like:

```


#! /bin/bash

sleep 20 && adept-notifier


```

chmod a+x myscript.sh

mv myscript.sh ~/.kde/Autostart/


it worked for me, but I had compis running on startup

---

