---
title: "Difference between 'spread all windows' and 'window spread' in hot corners"
date: 2014-01-29
forum: Desktop Environments
---

### Post by faust99 on 2014-01-29
In Unity Tweak tool, under the Hotcorners tab, there are options for (a) spread all windows and (b) window spread (among others). How do these  differ? They seem to do the same thing, which is to spread out all of the open application windows. It would be good to have a keyboard shortcut or mouse gesture (aside from clicking on the Dash) which allows one to spread the windows of just one particular application. Is this possible?

---

### Post by deadflowr on 2014-01-29
Windows spread will spread the windows on the current workspace only.
The spread all windows will spread the windows on all workspaces.
You can set keyboard shortcuts in the tab window spread.

Or if you want, in the program ccsm(compizconfig-settings-manager)
in ccsm go to scale > bindings.
In binding you can set the scale mode for keyboard, mouse-pressure on hot corner or mouse-click on hot corner.
Though, it's probably also doable in the tweak tool.

I personally set mouse-click on hot corner, because I tend to push my mouse to the edges far more than I should and setting it to cleck instead of simple pressure keeps it from spreading accidentally.

---

### Post by mc4man on 2014-01-29
> **faust99 said:**
>  It would be good to have a keyboard shortcut or mouse gesture (aside from clicking on the Dash) which allows one to spread the windows of just one particular application. Is this possible?

In theory it *could* be set in ccsm > scale > bindings > Initiate Window Picker for Window Group
However that's been broken since 11.04 or so & likely will never be fixed in compiz-0.9+

You can achieve the same thru compiz's dbus & commands plugins but due to some nonsense the command or binding will get unset every couple of days or so, a bit of a pita
If the command is integrated into compiz it will stick forever, however that is a bit to explain how to do...

(I do have ppa builds of compiz  for saucy & trusty where the  window picker for window group command  is integrated as a keyboard binding, currently ctrl+alt+z for single hand operation,  if interested will explain how to get/use

---

### Post by faust99 on 2014-01-29
Thanks guys, much appreciated.

---

