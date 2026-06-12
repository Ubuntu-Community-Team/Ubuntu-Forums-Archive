---
title: "Changing the color of the overlay which appears when resizing windows"
date: 2011-10-25
forum: Desktop Environments
---

### Post by jlebar on 2011-10-25
In 11.10 Unity, when I resize a window, I get a light-orange overlay showing me the new size.

Can I change this color?  I got rid of all the rest of the orange in my shell, but I haven't figured out how to get rid of this.

---

### Post by mc4man on 2011-10-25
If you are using compiz (unity-3d, gnome-session-fallback) then simply open ccsm (compizconfig-settings-manager) & in the "Resize Windows" plugin > General > Border Color 
This will open the settings directly, assuming compizconfig-settings-manager is installed

alt+f2, use command of  
ccsm -p resize

(if you haven't used ccsm before do yourself a favor & **don't** click on "Preferences" on ccsm's main page

If using gnome shell or unity-2d don't know, maybe something in gnome-color-chooser

---

### Post by jlebar on 2011-10-25
> **mc4man said:**
> If you are using compiz (unity-3d, gnome-session-fallback) then simply open ccsm (compizconfig-settings-manager) & in the "Resize Windows" plugin > General > Border Color

Ah, thanks!

Do you happen to know where the setting for the colors which appear when you move a window to the top of the screen and it becomes maximized are set?  I looked through my active compiz plugins and I don't see one which fits...

> (if you haven't used ccsm before do yourself a favor & **don't** click on "Preferences" on ccsm's main page

Yeah, I filed a bug on that a few days ago.  :)

---

### Post by jlebar on 2011-10-25
Ah, it's the Grid plugin.  Ofcourse.

Thanks again.

---

### Post by mc4man on 2011-10-25
> Yeah, I filed a bug on that a few days ago.
Have one filed also, no action - got a link to the one you did?
[https://bugs.launchpad.net/bugs/880679](https://bugs.launchpad.net/bugs/880679)

---

### Post by jlebar on 2011-10-25
Sure: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/875400](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/875400)

---

### Post by mc4man on 2011-10-25
The click on Preferences is not really 'crashing', though it may hang or function will return after 30 secs or so. It's just causing the Default profile to be loaded. 

If interested to see which profile you're on run ccsm from a terminal - line 5 - everyone starts in the 'unity' profile but may get switched to the' Default' one.

Ex. here
$ ccsm
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
....ect.

---

### Post by jlebar on 2011-10-25
$ ccsm
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity


I left it for a long time; in the bug, someone else left it for 20m.

---

### Post by mc4man on 2011-10-25
It certainly seems  then it can hang - if you look at your comment #4 - you'll see that you had been switched to the Default profile, something switched you back after that.

Many people are remaining on the Default profile - not all that different, has some plugins enabled that the unity profile doesn't & can be changed from other sessions like unity-2d & gnome-fallback

---

