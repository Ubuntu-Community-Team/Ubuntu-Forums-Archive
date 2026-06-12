---
title: "[IDEA] - Gnome Panel addon with AWN-type features"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by WinterWeaver on 2007-08-27
Hi everyone, /wave

I've been using Ubuntu for a little over a year now, and I'm in love.

I'm also one of those people that fool around with lots of eye candy and I constantly change the way my desktop looks :P

So lately, I've been using AWN, which is great, and I love it. Unfortunately one needs compiz or another compositor to run it effectively, and it's also not included in the default install.

**IDEA** 
A gnome panel applet which is very similar to AWN, without the animations of course. Something very simple, and clean. like the other gnome panel applets.

The main goal is to function as the window List applet does, except, that you only have the Icon/Launcher to represent the application. If the application is not open, and you click on the Icon, it functions as a launcher, and opens the app for you (basically exactly like AWN)

any thoughts if something like this exists or if someone is able to take up the challenge to create one?

ta, ^_^

WW

---

### Post by jordanmthomas on 2007-08-27
For a quick and dirty solution you could just make a launcher that runs a script like this:
```

#!/bin/bash
if pgrep $WHATEVERPROGRAM; then exit; fi
WHATEVERPROGRAM

```

If the program is already running, it exits, and if it isn't it launches it.  This wouldn't handle switching to the open program though, unfortunately, and I'm not sure how to implement that (with a bash script anyway).

Nice idea though.

---

### Post by WinterWeaver on 2007-08-27
Thanks for the suggestion ^_^

Cool, I don't know bash scripting much at all, so this is something nice to know. However, I like to be able to launch multiple program instances from the same launcher. So if I click a Icon again, it opens another instance.

At the moment I have a secondary panel, for which I increased the size to 50pixels, I enabled the hide buttons, cause I like being able to pull it from the side of the screen. It's also un-stretched. 
On this panel I place all my frequent apps, so this functions in a similair way as the script you suggested :)  ... it would be nice to have this function like a window list as well.

PS. On that note... is there a hotkey to pull a panel from the hide position, instead of clicking the hide button?

WW

---

### Post by BilliShere on 2008-06-18
I was hoping that we could possibly make a gnome applet that was like the drawer. except not as slow or ugly. basically stacks for gnome-panel!
it would look awesome and save space and time!

---

