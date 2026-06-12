---
title: "clock_screen0/prefs gone"
date: 2011-07-18
forum: Desktop Environments
---

### Post by whvw on 2011-07-18
For some reason the date in my clock has reverted to mm/dd-no year. When I go to root, it still displays as I set it: dd/mm/yyyy. Everyone says to use gconf-editor: ......clock_screen0/prefs. The only problem is that clock_screen0/prefs is no longer there. (it _is_ in root). What happened to it and how can I get it back? Is it possible to just copy the file root uses?:confused:

---

### Post by whvw on 2011-07-25
[B][COLOR=Red]SOLVED![/COLOR]
This is for ubuntu 9.10[/B] it might be the same for others..

The answer (which I found out for myself, actually the best way) is that _sometimes_ users on the _*same*_ installation will have a different file set up. In other words, even though other users on the _same_ installation will have the "screen0/prefs" file, others may not. Perhaps this is due to some update that doesn't spread itself across the whole system, I don't know. I'll leave that one for all the folks out there who have many orders of magnitude more knowledge about Linux than I. 
The solutions is, that the files (that you'll find after using "gconf-editor") are now: apps/panel/applets/applet_1/prefs. After clicking on "prefs", you enter your date/time preferences (that's the "%A %B..." stuff) in the "custom format" line (3rd from top). Then, on the 9th line, "format" you place the word "custom" (sans quotes). 
Hope this helps others who have endured and are enduring the same frustrations.

---

