---
title: "Shift switcher scrolls through two windows in one step"
date: 2007-09-11
forum: Desktop Effects &amp; Customization
---

### Post by bsander on 2007-09-11
I love the shift switcher. I mapped it to Super+Left and Super+Right, but when I start scrolling through my windows one step of the switcher actually scrolls through two windows :( Quite annoying when you have an even amount of windows open ;) Anybody know how to fix this?

---

### Post by praet on 2007-09-11
This probably has to do with multiple key presses getting interpreted by shift switcher when using the left and right keys in the main binding.
If you noticed, if you use the default binding <Super>Tab, THEN use the left or right keys (still holding super) then you can flip through windows.  I think what happens when you bind <Super>right to the action, that it is being interpreted by the action itself, and THEN AGAIN by the navigation code.

I can confirm this behavior on 0.5.2.

Maybe you should file a proper bug report to the plugin author.
edit: as the compiz repo I am using at this time is unofficial, reporting bugs to launchpad are not suggested, instead report issues with the repo maintainer who can file the bug upstream.

---

