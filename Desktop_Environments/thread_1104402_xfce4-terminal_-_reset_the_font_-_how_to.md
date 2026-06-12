---
title: "xfce4-terminal - reset the font - how to?"
date: 2009-03-23
forum: Desktop Environments
---

### Post by lays on 2009-03-23
Some time ago I messed with the fonts in the xfce4-terminal, so now when I launch a console app (MOCP, FPC) some of the fonts are different from the "default" one - Monospace 12. Deleting/movin the ~/.config directory didn't help, the settings don't reset. How to revert to the default terminal look to be able to set it from the beginning? 

Oh, and it looks like that:

[[IMG]http://img21.imageshack.us/img21/2954/screenshotsuh.th.png[/IMG]](http://img21.imageshack.us/my.php?image=screenshotsuh.png)

---

### Post by kerry_s on 2009-03-23
after you moved ~/.config did you log out and back in?

now in the terminal it looks like you have nedit running in it, did you change the launcher? if so, use synaptic to remove xfce4-terminal, then reinstall it.

---

### Post by lays on 2009-03-23
What is running on the screenshot, is FPC - Free Pascal IDE. I did move .config and .cache dirs and logged out and back in. The Xfce settings did reset, but when in the freshly-default terminal I ran FPC, the font problem still was there. Also, I tried using apt to purge xfce4-terminal and install it back in - didn't solve the flaw.

---

### Post by kerry_s on 2009-03-23
i'm not sure what you mean the font looks fine to me. looks like mono on my end in the screenshot.

---

### Post by lays on 2009-03-24
Look at the menu scrolled down and compare e.g. "Print" with "Print setup". The second one is Monospace 12.

---

### Post by denham2010 on 2009-03-24
Looking at the screenshot, you can see that they are all monospace font. every character lines up with the one above and below it in the menu.

The difference you are seeing between Print and Print Setup is that the Print option is 'greyed out' meaning it is not currently available for you to select, where the Print Setup option is available.

As with the other options in the menu. Some are 'greyed out' while others are not.

Cheers.

---

### Post by lays on 2009-03-24
Believe me, it really **did not** differ before I messed with the font settings. Maybe this will be a better example: 

(look at the curently played song on the file list)

[[IMG]http://img165.imageshack.us/img165/7060/screenshotb.th.png[/IMG]](http://img165.imageshack.us/my.php?image=screenshotb.png)

---

### Post by kerry_s on 2009-03-24
the problem can't be in xfce-terminal if you already reset the setting in .config, so you must have messed with the fonts in the main system settings, fonts are only set in a couple of places, look through all the settings.

the pic looks fine, the active song is bold to highlight it as active.

try in xterm> alt+f2 ,type> xterm
xterm fonts have to be set in .xdefaults so they should be stock.

---

