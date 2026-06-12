---
title: "terminal acting weird"
date: 2006-08-06
forum: Desktop Environments
---

### Post by nismohasan on 2006-08-06
i setup a tri boot with ubuntu;xubuntu;and xp and upgraded xubuntu to edgy

ubuntu and xubuntu share /home so i'm thinking a setting was overwritten.

how do i get it back to normal?

if i cd to /etc for example and ls files and folders are side by side
but if i enter my home dir /home/hasan

they run down the screen instead of side by side.

(screenshot for what i mean)

how do i get it to go side by side in my home dir again?

[[IMG]http://img54.imageshack.us/img54/5691/screenshotqf7.th.jpg[/IMG]](http://img54.imageshack.us/my.php?image=screenshotqf7.jpg)

---

### Post by firebadger on 2006-08-06
Is it not simply because you have a long file name in your home directory that doesn't leave room for more than one column?

---

### Post by kabus on 2006-08-06
There isn't a setting for this, the way ls lists files depends on font size and terminal dimensions.
The problem here is most likely that you have a few files with really long names in your home, so ls can't fit them in columns. All the files in /etc, on the other hand, have rather short names, so they fit.

---

### Post by nismohasan on 2006-08-06
ah yes you guys were right :-({|=

---

