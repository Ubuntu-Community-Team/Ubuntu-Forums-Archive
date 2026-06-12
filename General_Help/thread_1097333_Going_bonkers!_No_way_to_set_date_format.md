---
title: "Going bonkers! No way to set date format??"
date: 2009-03-15
forum: General Help
---

### Post by quixote on 2009-03-15
I don't want to change my timezone.  I just want my date in the panel formatted the way I want it.  This really shouldn't be that difficult!  I know Gnome devs think we should do everything their way, but this is ridiculous.  (I did say I was going bonkers.)

Based on other threads, I've tried setting it in the terminal  ```
Ssudo date +%Y %m %d, %H:%M
``` That echoes it in the correct format to the terminal, but doesn't show up in the panel.

The only other thing I saw that seemed applicable was a suggestion to get into gconf-editor, and under *apps > panel > applets > clock* to have a "custom_format" key (I had to make a new key) and put the desired string there.

That did nothing.  I see that there are *applet > clock* in all kinds of places, so maybe I didn't happen to hit the right one.

How the blankety-blank does one do what should be a perfectly simple thing?

---

### Post by quixote on 2009-03-18
Erm . . . bump?

---

### Post by fieroboom on 2009-03-18
I've never personally dealt with this on gnome, but I did a [quick google search](http://www.google.com/search?hl=en&safe=off&newwindow=1&q=gnome+panel+clock+format&btnG=Search) for "gnome panel clock format" and came up with:

[http://snuxoll.com/post/2008/11/16/custom-time-format-gnome-panel-clock](http://snuxoll.com/post/2008/11/16/custom-time-format-gnome-panel-clock)

I believe it uses the [strftime function](http://www.manpagez.com/man/3/strftime/), so you should be able to use any of those switches to format it exactly the way you want. I'm using Xfce right now, and it's Orage Clock applet was super easy to modify.
Hope that helps!
:D
-Paul

EDIT:
Just did [another google search](http://www.google.com/search?hl=en&safe=off&newwindow=1&q=gnome+custom+panel+clock+format&btnG=Search) for "gnome custom panel clock format" and found a couple more promising links, one of which is here on this forum:

[http://ubuntuforums.org/showthread.php?t=780676](http://ubuntuforums.org/showthread.php?t=780676)

[http://tips4linux.com/custom-clock-in-gnome/](http://tips4linux.com/custom-clock-in-gnome/)

Maybe that'll get your gears going! :D

---

### Post by quixote on 2009-03-18
Paul, thanks much for the links!  The earlier ubuntu forum was one I'd even seen, but I'd missed the other two.

Problem is: my gconf-editor doesn't seem to match anyone else's! :rolleyes:  I'm running Intrepid, which I assume is pretty standard by now.

I have: apps > panel> default_setup > applets > clock.  There's no "prefs" menu item.  And under "clock" there's no "format" or "custom_format".  I actually added both those keys, and entered "format   custom"  and "custom_format   strftime-string-whatever-it-was"  Did nothing, of course.

I had another stab at looking for the setting and was tickled to find "schemas > apps > clock_applet > prefs"  I got excited.  Sure enough, there's both "format" and "custom_format" both set to <schema>.  I right click and . . . the damn fool thing won't let me edit them!

Gaaa.

This is linux.  There has to be a command line way to keyboard this thing into submission!  Given that you got further googling than I did, I'll keep trying that.  Any further ideas will be much appreciated!  Thanks!

---

### Post by quixote on 2009-03-18
Oh for cryin out loud, I just got what the difference was:  I was running gconf-editor as sudo, figuring that was necessary.  If you run it as a user, the menu items the other posts refer to are there, I can enter my strftime string, and everything is beautiful.

Thanks for getting me on the right track.

---

### Post by jwbrase on 2009-03-18
I found this thread and started fiddling around with the date format, and discovered something weird. The parameters that are supposed to show the second, like %S and &s, only update every 60 seconds, so they're somewhat useless.

---

### Post by hikaricore on 2009-03-18
One of the wonderful things about Gnome is that the Gnome dev's decided that you the user don't need to modify things such as the panel text colour, the clock format, or things such as the number of flying toasters on your screensaver.  So..... you just aren't presented with the options to do so and must dig through the mess that is gconf.  >.<

---

### Post by jwbrase on 2009-03-18
> **hikaricore said:**
> or things such as the number of flying toasters on your screensaver. 

That's why I use xscreensaver instead of the default Gnome screensaver program.

---

### Post by kenkaku on 2010-04-08
> **jwbrase said:**
> I found this thread and started fiddling around with the date format, and discovered something weird. The parameters that are supposed to show the second, like %S and &s, only update every 60 seconds, so they're somewhat useless.

If you use %T instead of %H:%M:%S, it will display seconds which update at 60Hz.

---

