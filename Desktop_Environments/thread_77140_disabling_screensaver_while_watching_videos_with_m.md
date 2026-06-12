---
title: "disabling screensaver while watching videos with mplayer"
date: 2005-10-16
forum: Desktop Environments
---

### Post by wezzer-foo on 2005-10-16
Hi all,

I have a question, is it possible to disable screensaver while watching videos with mplayer? And I would prefer that kind of solution, that I don't have to do everytime I watch videos.

---

### Post by kvidell on 2005-10-16
I'd actually like to know that very much.
I was watching Dirty Shame with a friend of mine the other day using```
mplayer -fstype fullscreen -fs
```and every 10 minutes I'd have to jiggle something so that it wouldn't go into screensaver.

My thought is maybe you can add an alias or something in the mplayer rc file that sets an environment variable that instructs xscreensaver not to run, then unsets itself as soon as mplayer terminates?
- Kev

---

### Post by taurus on 2005-10-16
Place your cursor over the mplayer's window and right click the mouse.  Go down to Preferences and at the last option, Misc (I think), there is an option in that window to turn off xscreensaver...

---

### Post by wezzer-foo on 2005-10-16
[QUOTE=taurus]Place your cursor over the mplayer's window and right click the mouse.  Go down to Preferences and at the last option, Misc (I think), there is an option in that window to turn off xscreensaver...[/QUOTE]

Well that doesn't work because I don't have any gui installed.

---

### Post by yage on 2005-10-16
Dunno if this work but you can try putting this line in your /home/username/.mplayer/config file
```
stopxscreensaver = "yes"
``` Since this is the line set when you have the gui installed.

---

### Post by taurus on 2005-10-16
You don't have gmplayer which is technically linking to mplayer...

---

### Post by wezzer-foo on 2005-10-16
[QUOTE=yage]Dunno if this work but you can try putting this line in your /home/username/.mplayer/config file
```
stopxscreensaver = "yes"
``` Since this is the line set when you have the gui installed.[/QUOTE]

That didn't help neither... Does it matter that I have this line in the same config?
```
vo=gl2
```
After I installed ATI binary driver fullscreen didn't work unless I had this line in the configuration file.

---

### Post by yage on 2005-10-16
After searching google i found this line```
stop-xscreensaver=1
``` it states that this is only for X11 but i don't see how mplayer should work without X11? Try it... tell us if it works :)

---

### Post by wezzer-foo on 2005-10-16
[QUOTE=yage]After searching google i found this line```
stop-xscreensaver=1
``` it states that this is only for X11 but i don't see how mplayer should work without X11? Try it... tell us if it works :)[/QUOTE]

It seems that it works! Thanks!

---

### Post by yage on 2005-10-16
Great! :D

---

