---
title: "after installing compiz settings manager, panel and top bar are gone"
date: 2011-10-25
forum: Desktop Environments
---

### Post by short4lif2 on 2011-10-25
I installed compiz settings manager from the software center, and simply by clickin on the preferences button the right, everything is gone.  My desktop is just a bare nautilus window, and i got into chrome by ctrl+alt+t ing into a terminal.  Any suggestions on getting my settings back to where they were?

I am running a Lenovo Thinkpad r61e without any problems so far on 11.10 (except for a sound problem which i cleared up recently.)


Thanks

---

### Post by mc4man on 2011-10-25
As soon as you clicked on ccsm > Preferences you where switched from the 'unity' profile to the "Default' profile

By default the "Default" profile doesn't have the Unity plugin ebabled, hence no launcher & panel

Your choice is whether to continue to use the "Default" profile or return to the "unity" profile.

To continue using the "Default" profile just log back into the ubuntu session > open a terminal > enter ccsm & enable the Unity plugin

==================================================================
If you want to go back to the orig/default unity profile there are a couple of ways, easiest is - 
login in to the ubuntu session as above, open a terminal and go
```
nautilus .config/compiz-1/compizconfig
```
Inside will be a file named config, open it up & delete it;s contents, save.
Then go Ctrl+Alt+Delete & log out & back into the ubuntu session

If you go back into ccsm > Preferences again while in the "unity" profile the whole thing will start over.
(there is a way to add a unity profile into ccsm > Preferences, though not much to be gained

Here's a bug I filed on this bit of a mess, may have explained a better, may not have...
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/880679](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/880679)

---

### Post by short4lif2 on 2011-10-25
Worked!  thank you, good sir, I appreciate.

---

### Post by sklero on 2011-10-25
I had same problems...
Digging other threads I found this:
Open terminal (CTRL-ALT-T)
Run ccsm 
Go to Desktop section (left) and just enable UNITY PLUGIN (in case resolve conflicts)
It was right for me!

---

### Post by swapii on 2011-10-25
> **mc4man said:**
> As soon as you clicked on ccsm > Preferences you where switched from the 'unity' profile to the "Default' profile

By default the "Default" profile doesn't have the Unity plugin ebabled, hence no launcher & panel

Your choice is whether to continue to use the "Default" profile or return to the "unity" profile.

To continue using the "Default" profile just log back into the ubuntu session > open a terminal > enter ccsm & enable the Unity plugin

==================================================================
If you want to go back to the orig/default unity profile there are a couple of ways, easiest is - 
login in to the ubuntu session as above, open a terminal and go
```
nautilus .config/compiz-1/compizconfig
```Inside will be a file named config, open it up & delete it;s contents, save.
Then go Ctrl+Alt+Delete & log out & back into the ubuntu session

If you go back into ccsm > Preferences again while in the "unity" profile the whole thing will start over.
(there is a way to add a unity profile into ccsm > Preferences, though not much to be gained

Here's a bug I filed on this bit of a mess, may have explained a better, may not have...
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/880679](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/880679)


Hey thanx     it worked....
bt     it needed   to be used  with "alt+ctrl+f1" (console mode)....

if   error is given that directory not found then try 'compiz' insted 'compiz-1'...
thanks..........  :)

---

### Post by ershad ali on 2011-10-26
I had a same problem even worth , all of my icons has disappeared but i have done what you say and restarted and bingoooo every thing is ok
thank you so much

---

