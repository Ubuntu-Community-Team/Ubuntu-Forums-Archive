---
title: "Default gnome themes and gdm went ugly... HELP"
date: 2010-08-21
forum: Desktop Environments
---

### Post by papajonesy on 2010-08-21
After installing a few different engines (murrine, equinox, pixbuf) my default gnome themes like ambiance, radiance, dust etc have completely lost their window style. Even the gdm login went ugly, look at my screenshot. Please help.

---

### Post by papajonesy on 2010-08-21
No such luck. :( any other ideas?

---

### Post by N00b-un-2 on 2011-04-27
it looks as though you're gtk theme is reverting to a default.  Did you perhaps accidentally uninstall some gtk engines?  If so you may want to try reinstalling them
```
sudo apt-get install gtk2-engines*
```

---

### Post by ankspo71 on 2011-04-28
Hi,
If it seemed to happen for no reason at all, then it looks like a gnome-settings-daemon problem... which is getting to be a common problem. 

Try running gnome-settings-daemon in the terminal and see what happens. It should return your theme back to the way it was, or report some error messages. You can also look through the hidden file in your home folder called ".xsession-errors" to help further identify the cause of the problem.

I've seen some people mention that reinstalling gnome-settings-daemon helped solve their problem with it, and others said that making a script to have it run on startup after a short delay helped solve their problem with it too.

Here is a large thread about a similar problem:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)
There is probably some more useful advice you can use in there.
Hope this helps.

PS: The new theme engines might not have been compatible with the current theme engines and removed them in the process, like the above poster mentioned. Do the newly installed themes work?

---

### Post by Krytarik on 2011-04-28
@ankspo71: *N00b-un-2* just dug out an old thread, I bet the OP did already either fix it or reinstall. ;-)

---

### Post by ankspo71 on 2011-04-28
Oh okay, thanks :)

---

### Post by demilord on 2011-05-13
I had this problem... just for people who has the same problem and use search...

open terminal and type in a couple of times  < killall nautilus >

logout reboot didnt help at me

---

### Post by Krytarik on 2011-05-13
Just for completeness, threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Greetings.

---

