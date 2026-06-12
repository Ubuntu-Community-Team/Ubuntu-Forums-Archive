---
title: "gnome-screenshot shortcuts"
date: 2011-04-01
forum: Desktop Environments
---

### Post by chower on 2011-04-01
I'm working on making my desktop a little faster by integrating some shortcut keys for common tasks.  One of the things I use alot is gnome-screenshot.  I see from the man page, that I can use a -a or --area to grab just an area of the screen, works great when I run gnome-screenshot --area from a command line, but when I try to create a shortcut with the same parameters under System --> Preferences --> Keyboard shortcuts, it just takes a screenshot of the entire desktop.  Using the -w or --window works as expected.  I'm running a fairly fresh install of 10.10.

Any ideas?  Here's a screenshot of how I have it setup:

---

### Post by Krytarik on 2011-04-01
I can reproduce that behaviour at my system, running 10.04, like stated. Really weird!

And I even found a bug report regarding that:
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/549935](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/549935)

But I also found a workaround for that:
```
sleep 0.02; gnome-screenshot --area
```That delays its execution for 0.02 seconds. At my system, this is just enough, but you need to fine-tune this to your own system.

If you have a launchpad account, please enlist yourself as "affected", I've done so, currently 3 people (incl. me).

I also left a comment including the found workaround.

Greetings.

---

### Post by chower on 2011-04-02
Gave that a shot, but didn't work on my system.  Didn't even do the whole desktop thing.  Is there any sort of debug for the keyboard shortcuts?  I looked through the /var/log/gdm/* logs and didn't see anything obvious.

---

### Post by Krytarik on 2011-04-02
But this is still about a keyboard shortcut, right?

If you want to run it through a launcher, you need to put the command like this:
```
sh -c "sleep 0.02; gnome-screenshot --area"
```Otherwise, simply nothing happens.

Also, please see my edited post regarding the fine-tuning, I only did this afterwards.

---

### Post by chower on 2011-04-02
Yea, still from keyboard shortcuts.  I did some playing around with it and if the shortcut command is "gnome-screenshot --interactive --area" it brings up the take screenshot dialog with the area option set.  It'll work for me as a workaround, wish I knew how launching it from a keyboard shortcut is any different than from a terminal.

Edit: Wrote a very simple shell script and applied that to the shortcut and it works:
```

#!/bin/sh
sleep 0.1
gnome-screenshot --area

```

Without the sleep, the script worked when ran from a terminal, but not from the shortcut.  Once I added the sleep it worked fine.  I'd like to know the reason, but in any case accomplishes the goal I was after.

Thanks!

---

### Post by Krytarik on 2011-04-02
Ah, this is funny!! :D Obviously, the set command gets run in a different environment when set in "Keyboard Shortcuts" (generally handled by Metacity) than when set in Compiz' options. I only set it in the latter before. Apparently, Compiz runs those commands in a shell environment by default, whereas 'Metacity' runs those commands in similar or same environment like the launcher commands are getting run in.

I still don't know exactly how those both setups are interconnected, and which app actually runs which commands. I know that both share the same keys in Gconf, but on the other hand either app doesn't 'see' the shortcuts set up by the other app. Really curious!

---

