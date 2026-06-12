---
title: "Ubuntu 10.10 looks like an older version"
date: 2011-04-08
forum: Desktop Environments
---

### Post by AndrewD257 on 2011-04-08
When I boot up ubuntu 10.10, at first it looks fine,  but after just a few minutes the color scheme will change to look like older versions of ubuntu (like 9.04).

By this I mean that the top and bottom bar turn light grey instead of dark grey, and that icons and scroll bars in open windows look old.  

Here is a screen shot of what it looks like.  Keep in mind that this is in fact 10.10
[IMG]file:///home/andrew/Desktop/Selection_001.png[/IMG]

Another interesting thing is that when I go to system->preferences->appearance->visual effects, none of the three options are checked (though compiz and emerald are still working fine).  The weird thing, though, is that just opening the appearance window seems to temporarily solve the problem.

any ideas would be appreciated.

---

### Post by reborn7778 on 2011-04-08
> **AndrewD257 said:**
> When I boot up ubuntu 10.10, at first it looks fine,  but after just a few minutes the color scheme will change to look like older versions of ubuntu (like 9.04).

By this I mean that the top and bottom bar turn light grey instead of dark grey, and that icons and scroll bars in open windows look old.  

Here is a screen shot of what it looks like.  Keep in mind that this is in fact 10.10
[IMG]file:///home/andrew/Desktop/Selection_001.png[/IMG]

Another interesting thing is that when I go to system->preferences->appearance->visual effects, none of the three options are checked (though compiz and emerald are still working fine).  The weird thing, though, is that just opening the appearance window seems to temporarily solve the problem.

any ideas would be appreciated.

just click-right mouse, then appear "change desktop background. here you go.

---

### Post by Copper Bezel on 2011-04-08
It's a common problem with a quick fix by adding a command to your startup applications - see [this]("http://ubuntuforums.org/showthread.php?t=1722179&highlight=daemon") thread.

---

### Post by mcduck on 2011-04-09
> **AndrewD257 said:**
> 
Another interesting thing is that when I go to system->preferences->appearance->visual effects, none of the three options are checked (though compiz and emerald are still working fine).

If you have changed any Compiz setting yourself (like you must have done since you are using Emerald) then you aren't using any of the visual effects presets that are available in the Appearance dialog. So none of them is even supposed to be enabled. ;)

The settings there switch between Metacity ("None") and two pre-configured Compiz setups.

---

### Post by AndrewD257 on 2011-04-09
Thanks for all your quick responses.  I tried adding that command at start up, like it says in the other forums, but it is still happening.  I always happens about 10 or 15 seconds after I boot up.  Any other Ideas?

---

### Post by marin123 on 2011-04-09
are you maybe running something as sudo? it sometimes happens when i run update manager and open new windows. it should go away few minutes after you stop running sudo apps...

---

### Post by stinkeye on 2011-04-09
If you want to try the command that **Copper Bezel** linked to in 
in startup preferences, use...
```
bash -c 'sleep 10s; gnome-settings-daemon && killall nautilus'
```


This entry works for me (much the same really)
```
bash -c 'killall -9 gnome-settings-daemon; gnome-settings-daemon; nautilus -q'
```


Next time it happens just test to see if the command fixes it, by running in the terminal.
It's a fix for the gnome-settings-daemon not starting
which appears to be happening to a lot of users.

---

### Post by AndrewD257 on 2011-04-09
Ok, I tried both of those commands, and no luck on either of them.  The first one will fix the problem when I use it in terminal after the problem has happened, however.  The second one will not run, as it says 
"gnome-settings-daemon: no process found"

could that have something to do with it? any ideas?

---

### Post by Copper Bezel on 2011-04-09
> Thanks for all your quick responses. I tried adding that command at start up, like it says in the other forums, but it is still happening. I always happens about 10 or 15 seconds after I boot up. Any other Ideas?

You could extend the delay to match this, but it would be unpredictable and you'd still have a flicker even if the timing was perfect. For now, I'd say just create a launcher for the command (without the delay.) It's an odd bug, but you're not alone in experiencing this. I've personally only seen it happen at startup, not afterward.

---

### Post by AndrewD257 on 2011-04-09
Ok, I'll probably just do that.  Thanks to all you guys for your help.  I sure do love this forum.

---

### Post by Krytarik on 2011-04-10
> **marin123 said:**
> are you maybe running something as sudo? it sometimes happens when i run update manager and open new windows. it should go away few minutes after you stop running sudo apps...
That happens if the theme you are using is not installed system-wide, in "/usr/share/themes"; and "/usr/share/icons" for icon themes. The effect is that 'root' doesn't know about your user specific themes, and therefore the default fallback theme "Raleigh" gets applied instead, but only to apps that are run as root. Whereas the other fallback scenario users are experiencing with those bug affects all windows, besides some other settings as well.

---

