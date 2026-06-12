---
title: "KDE panels: no autohide"
date: 2005-12-19
forum: Desktop Environments
---

### Post by runlevel0 on 2005-12-19
I just upgraded to KDE 3.5. 

In my last setup I was using the autohide function on two of my three panels.
After changing to KDE 3.5 the panels do close but they don't react when I try to open them again.

I indeed have to open the panel's config dialog and disable 'autohide' to be able to use them.

Any workaround?
Or should I better take a chance with Superkaramba to emulate 
KDE's panels?

---

### Post by One Quick Question on 2005-12-20
Hmm, that's odd. I don't have the same issue.
Are you sure the "Raise when the pointer touches the screen's: _____" setting is correct?

---

### Post by ace2005 on 2005-12-20
Yea Strange, i don't have it either

In the hiding section have you selected "Hide Automatically" and put the time to immediately and unchecked everything else?

Those are the settings i use, or you could rename ~/.kde to to ~/.kde_backup and see if it is the config causing the problem or a problem with KDE itself

---

### Post by Harleen on 2005-12-20
In KDE 3.5 the standard behaviour has changed a bit. The menu bar now only opens, if you move the mouse pointer to the left lower corner of the screen and not just to the lower border as before. I found that irritating, too.
This can be turned off in the panel settings so it works like it used to.

---

### Post by runlevel0 on 2005-12-20
Thanks to all, it works.
I enabled autohide and the correct unhide settings from the pulldown menu: I have set one to unhide when the mouse touches the  bottom of the screen and the other when the mouse touches the right side of the screen.

The problem was that the unhiding of one panel seems to interfere with the others. Ths solution was setting the animation speed to the max. Once it's working I changed it back to a slower speed and it works. The animation is not very smooth, however.

---

