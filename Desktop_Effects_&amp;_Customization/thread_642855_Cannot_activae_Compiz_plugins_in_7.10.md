---
title: "Cannot activae Compiz plugins in 7.10"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by JoakimP on 2007-12-17
I have a problem that has occurred recently.
When I start ccsm all the checkboxes to activate plugins are greyed out.
If I run it with gksudo it looks OK but no actual changes are made (only for root I guess).
I can change it as root, save a profile and import it into the user ccsm, but that is a bit tiresome.

I have quite recently added another user to the system, but I'm not suer that the problem occured then. I'm running Gutsy on a Dell D830 by the way. Graphics work fine with Compiz.

I would be happy if anyone has any ideas about this.

---

### Post by shearroller on 2007-12-17
Try this:

Click on:

 SYSTEM/PREFERENCES/ADVANCED DESKTOP EFFECTS SETTINGS

Once you have CCSM open click on PREFERENCES then look at the top you will find two (2) tabs, click on the tab labelled PLUGIN LIST.  On the resulting window be sure AUTOMATIC PLUGIN SORTING is checked.  Since your plugins are all greyed out chances are it's not checked!  While playing around with CCSM I purposely unchecked this option to see what effect it would have - it caused every plugin to be greyed out!

Live and learn.

Mike

---

### Post by muadnu on 2007-12-18
Thanks for that! I installed some new plugins and suddenly all the options were grayed out, but this fixed it...

---

### Post by andrewsomething on 2008-01-13
Google + Ubuntu Forums is a life saver! I had this exact problem. I googled "plugins greyed out ccsm," and this was the first hit. Solved in seconds1 Thanks....

---

