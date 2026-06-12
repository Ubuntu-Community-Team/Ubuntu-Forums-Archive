---
title: "[SOLVED] compiz settings manager not working?"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by luke16 on 2007-12-11
First of all, whats the correct compiz settings manager to get and use? I found 2 of them with synaptic, one of them shows up on the system>preferences menu as gl desktop (and on synaptic as gnome compiz manager), and the other as advanced desktop settings. Neither one of them seems to do anything (tried installing and using them exclusively of each other), except that I now have only one virtual desktop. When I change the settings in them, nothing happens and there is no "apply" button. For the latter, I tried disabling a bunch of plugins, and they all still work afterwards, even after I close the window. It just doesn't respond to what I tell it to. Am I supposed to restart the computer for the changes to take effect or something?

---

### Post by schmildo on 2007-12-11
I'm no guru at this, when I did it i was confused also, and i'm still not sure, but:

I'm running Xubuntu (whcih apparently has something to do with gnome) I was given two commands to play around with:

compiz --replace gconf &
compiz --replace ccp &

They seemed to make the fancy pancy desktop effects work (except for the cube)
...and even when I did use these commands my title bars went missing and wouldnt come back so I had to run this...

gtk-window-decorator --replace &

...every time I booted... I got cranky and had another look in synaptic. I uninstalled the compiz manager, and installed the gnome-compiz-manager (i think it's called) and then I rebooted.

And now I dont have to run stupid command lines for it to work, and the title bars are working.

The "gnome-compiz-manager" installs the "GL Desktop" program, which has alot less options than the normal thingy, but at leeast it works, and i think the effects are supposed to work the moment you tick the box in the application, there is no apply button.

---

