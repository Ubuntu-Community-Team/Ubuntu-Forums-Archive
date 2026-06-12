---
title: "Make windows zoom out"
date: 2012-09-01
forum: Desktop Environments
---

### Post by rks171 on 2012-09-01
I used to use Ubuntu 10.04.  A great feature I utilized was making all the windows (in all of my workspaces) zoom out by pressing the super+a key combo (windows key + a).  Then I could pick a window and I would automatically be switched to that workspace.  Now, in Ubuntu 12.04, the super key brings up the dash.  I can press super+s to zoom out my workspaces, but this isn't the same.  It doesn't show all the windows, just a snapshot of all the workspaces.  Was this feature switched to a different key combo or do I have to do something to enable it?

---

### Post by rks171 on 2012-09-01
Nevermind.  It looks like the key binding was switched to "super+w".  I believe this 'zoom out' mode is called 'expo mode'.

EDIT:  On further examination, "super+w" doesn't do what I want it to.  It only zooms out windows in the current workspace.  I want to zoom out all windows in all workspaces.  Does anybody know how to do that in 12.04?

---

### Post by Krytarik on 2012-09-01
What you are searching for is a feature of the "Scale" plugin of Compiz, particularly "Initiate Window Picker For All Windows". To check/change its key binding, install CompizConfig Settings Manager, if you haven't already, and go to "CCSM -> Window Management -> Scale -> Bindings".

Regards.

---

### Post by rks171 on 2012-09-03
Thanks for the reply.  I checked and this setting is already enabled.  It is mapped to the "super+w" binding, which I already tried.  The "Initiate window picker for all windows" and "Initiate window picker" tools both do the same thing, which is to only show windows on the current workspace instead of all of them.  A little more research revealed that this is actually a [bug ]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933776").  

There is supposedly a fix by adding [this ppa.]("https://launchpad.net/~bsantos/+archive/ppa")  I added it and did ```
sudo apt-get update
``` and then ```
sudo apt-get install compiz
```.  I'm not so sure if that second command is what I needed to get the fix.  It's not working so far, but maybe I need to log out of my profile for setting to take effect?

UPDATE: Seems that was the problem.  I logged out and back in and then changed the key binding to "alt+super+w" instead of the usual "super+w" and it works exactly as it should now.

---

