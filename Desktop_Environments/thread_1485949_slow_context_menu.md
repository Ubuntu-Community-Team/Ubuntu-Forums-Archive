---
title: "slow context menu"
date: 2010-05-17
forum: Desktop Environments
---

### Post by nerdy_kid on 2010-05-17
hello everyone, my context menu in dolphin/konquerer is very slow -- 2-3 seconds to pop up.  I have a dual core 1.4ghz pc, so pc speed is not an issue.  My cpu pins during the delay that the context menu takes to pop up.  I ran valgrind --tool=callgrind dolphin and attached the two files that it produced.  I viewed them in kcachegrind but i dont know what to make of the data.  I'm gonna switch distros if i cant fix this :(  dont want to though, I like ubuntu!


{edit} ok so i couldnt attach them but i uploaded them to my server here:  [http://71.184.250.132/kcachgrind/](http://71.184.250.132/kcachgrind/)

---

### Post by nerdy_kid on 2010-05-18
help please...

---

### Post by nerdy_kid on 2010-05-19
bump

---

### Post by nerdy_kid on 2010-05-19
I have

removed all file templates, no change.
removed all custom file associations, no change.
deleted .local and .config. no change.
tried new user, no change.
tried changing kde theme, no change.
disabled my nvidia driver, no change.
tried changing view modes in dolphin, no change.
changed icons in dolphin, no change.
disabled nepomuk/strigi, no change.
rmed /tmp/, no change.
running out of ideas...

it is only when i right click folders/file icons though. I can right click a blank space in dolphin and it works right, I can also enable the tree view side bar and right click works like a charm. Right click also works as expected in open as/save as dialogs.


also when i try changing file permissions/icons, the "updating system configuration" progress bar loops, and in the case of changing file assocations, does nothing. maybe this is related somehow? I get "kbuildsycoca4(6670) parseLayoutNode: The menu spec file contains a Layout or DefaultLayout tag without the mandatory Merge tag inside. Please fix your file." when i try updating the icons. Maybe i should switch distros  :(

---

### Post by Zorael on 2010-05-20
I'd suggest you try **#kubuntu-devel** on **irc.freenode.net**; this sounds pretty technical.

---

### Post by nerdy_kid on 2010-05-22
> **Zorael said:**
> I'd suggest you try **#kubuntu-devel** on **irc.freenode.net**; this sounds pretty technical.

thanks :)

thanks to a admin on kde forums, i have managed to cut the delay down to 1/2 sec; still irritating, but better then 2-3 secs.

---

