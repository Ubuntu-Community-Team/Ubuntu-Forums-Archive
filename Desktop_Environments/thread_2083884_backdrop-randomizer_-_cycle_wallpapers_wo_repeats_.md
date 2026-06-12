---
title: "backdrop-randomizer - cycle wallpapers wo/ repeats (xfdesktop)"
date: 2012-11-13
forum: Desktop Environments
---

### Post by graysky on 2012-11-13
**_What is it_**
Backdrop-randomizer is a companion for xfdesktop which randomly cycles through wallpapers without repeating them until all have been displayed once. I wrote it specifically for xfce4 users displaying desktop pics with xfdesktop. If this is you, read on.

_**Rationale and Gap**_
Xfdesktop has a gap currently: it does not keep track of which images in a list are displayed as "backdrops" to the DE.  The result is that some images in a list get displayed frequently while others are rarely displayed.  A more robust implementation of the random background feature should randomly display an image in the list and _not_ repeat it until all list members have been displayed at least once.  This bothered me so much that I [opened a bug/enhancement](https://bugzilla.xfce.org/show_bug.cgi?id=9488) with upstream. 

...backdrop-randomizer fills this gap :)

**_How it works_**
Each time you or cron calls the script, it will randomly select a picture from your list to display. It will then remove the selection from the list so as not to repeat the same pic twice per cycle. When backdrop-randomizer sees you have only one pic left in your list, it regenerates the list anew and continues to cycle. The net effect is an endless rotation of your pics without a repeat.

**_Links_**
Github: [https://github.com/graysky2/backdrop-randomizer](https://github.com/graysky2/backdrop-randomizer)

Feedback is welcomed!

---

