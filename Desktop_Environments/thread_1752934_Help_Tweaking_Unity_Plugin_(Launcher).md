---
title: "Help Tweaking Unity Plugin (Launcher)"
date: 2011-05-08
forum: Desktop Environments
---

### Post by TurtleKing on 2011-05-08
Any idea on how to remove the window switcher from the unity launcher? The google-fu is giving me a ton of Operating System-Window + Unity results.](*,)

Also, me and my bro have been busting our heads trying to figure out why the windows title bar on Unity think it's a great idea, that even though you set the window buttons to show on the right, when maximizing they return once again to the left-side (on the top panel?). Any idea on how to stop this behavior from occuring?

I tried looking through CompizConfig Setting Manager, but didn't notice any option that pointed to this section. Also, I tried hitting it with a newspaper but the monitor keeps getting in the way.:confused:

---

### Post by TurtleKing on 2011-05-10
bump.

---

### Post by mc4man on 2011-05-10
> Any idea on how to remove the window switcher from the unity launcher? 
If you only use 1 workspace then it will disappear, other than that no
(unless you can find some source edit to make it disappear w/ more than one ws
> 
you set the window buttons to show on the right, when maximizing they return once again to the left-side
Nothing to be done to alter that in natty

---

### Post by Frogs Hair on 2011-05-10
I have my cube working and the switcher now acts as an expo button . There is a question posted at Launchpad.net about this with no answer .

---

### Post by mc4man on 2011-05-10
> I have my cube working and the switcher now acts as an expo button
The ws switcher in the unity launcher has always been 'expo', also seen w/ super+s

---

### Post by TurtleKing on 2011-05-11
> **mc4man said:**
> If you only use 1 workspace then it will disappear, other than that no
(unless you can find some source edit to make it disappear w/ more than one ws

Nothing to be done to alter that in natty
I only use one workspace (not sure how to disable the others). This must be what OMG-Ubuntu was referring to in terms of limited customization. I guess I will stick to Ubuntu Classic.

---

### Post by mc4man on 2011-05-11
> **TurtleKing said:**
> I only use one workspace (not sure how to disable the others). This must be what OMG-Ubuntu was referring to in terms of limited customization. I guess I will stick to Ubuntu Classic.
Can be done either in ccsm > general options > Desktop size (set both hort. and vert. to 1 (ccsm is compizconfig-settings-manager

Or quite easy in gconf-editor - see screen, r. click on the 2 keys > edit

Or 2 simple commands - 

```
gconftool-2 -s /apps/compiz-1/general/screen0/options/hsize --type=int 1
```

```
gconftool-2 -s /apps/compiz-1/general/screen0/options/vsize --type=int 1

```
Then log out/in
commands must be run in unity login to affect unity ws #

Edit:
> limited customization.
Somewhat in the eyes of the beholder...

---

### Post by TurtleKing on 2011-10-18
Update:
CCSM no longer has the desktop size option.

---

### Post by mc4man on 2011-10-18
> **TurtleKing said:**
> Update:
CCSM no longer has the desktop size option.

I see it here, using the current ccsm package, 0.9.5.92-0ubuntu1

---

### Post by TurtleKing on 2011-10-19
Weird.:confused: It wasn't there earlier when I checked. I guess it got fixed after an update or something. Thanks for double-checking it.

---

