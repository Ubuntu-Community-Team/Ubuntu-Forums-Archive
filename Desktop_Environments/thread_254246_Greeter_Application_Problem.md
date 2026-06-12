---
title: "Greeter Application Problem"
date: 2006-09-09
forum: Desktop Environments
---

### Post by rupes on 2006-09-09
At the moment whenever I boot ubuntu it says:

"The greeter application appears to be crashing. Attempting to use a different one."

I click OK and it loads the Gnome Login Window. I think this problem was caused recently when I tried to use a custom splash screen. 

Basically what I want to do is to have it back to normal.

Thanks

Rupes

---

### Post by cptnapalm on 2006-09-09
How about that... I came here for exactly this same reason.

I have partial solution.

First, what is happening is that gdm.conf and/or gdm.conf-custom is getting messed up.  Don't ask how, because I don't know.  Easiest solution is to purge gdm and reinstall it.  I did it from Synaptic.  This portion works fine.

What I don't get is why gdm going haywire messes up the settings for other apps.  For example, Firefox lost my bookmarks and my settings.  I copied one of the bookmark backups and wiped out the .mozilla folder and later imported them.  But all other settings are lost.  AND aMule's settings are screwed up as well; it reset the directory and the local settings.

I'm thinking Gnome (perhaps gconf related) is to blame.

The joys of an integrated desktop.

:?

EDIT: Now I've noticed that my font settings were changed too.  I need a 'smash someone else's head into a brick wall' smiley.

---

