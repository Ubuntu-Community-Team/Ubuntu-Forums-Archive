---
title: "Home icon on Unity launcher broken since upgrade"
date: 2011-11-16
forum: Desktop Environments
---

### Post by psypher on 2011-11-16
HI All,

Since installing Oneiric, fresh install not upgrade, my nautilus home icon in the launcher is broken. I used the same home folder I had in natty though.

When i click home it opens a new icon on the launcher right at the bottom and any subsequent nautilus windows all group under that icon. So now I have 2 nautilus icons in the launcher instead of one. If I log into a new profile this issue does not occur.

Does anyone know how to fix this issue? I have tried removing and re-adding the home icon both from /usr/share/applications and from the dash

Thanks

---

### Post by lolpenguin on 2011-11-16
This is due to one of the following two:
Files is pinned to the launcher but Home Folder is default.
Home folder is pinned to the launcher but Files is default.
I have experienced this myself. To solve this, right click on the nautilus icon at the bottom, and select "Keep in launcher", then right click on the one at the top and deselect Keep in launcher.
BTW both Files and Home Folder open Nautilus, just they are different app launchers

---

### Post by psypher on 2011-11-16
Hmm, looks like I inadvertently fixed it myself. Switching to a new user and trying the icon there and switching back sorted me out. This is preliminary test, might be broken again when I reboot

---

### Post by Steeperton on 2011-11-16
Do you have a custom quicklist for the home button? If so, remove:

```
OnlyShowIn=GNOME;Unity; 
```

from nautilus-home.desktop 

[http://ubuntuforums.org/showthread.php?t=1864679](http://ubuntuforums.org/showthread.php?t=1864679)

---

### Post by psypher on 2011-11-17
BTW false alarm, after reboot it's back. I did try remove that line from nautilus-home.desktop and re-added it, didn't fix the issue

---

### Post by Angus Podgornie on 2011-11-20
Hello,
I've had the same problem this evening, only the icon for my second "home" application was the Nautillus shell.
This  occured while I was trying to create a second tab, to copy some files to my dropbox folder. Same as what you did, I tried to unpin then pin again the "home" icon, then tried to redo what seemed to be the cause, and right-clicked the side-bar to open a folder in a new window. It worked.
Since I fell upon this thread, I thought I might as well share "my" solution to the problem. I hope my explanations didn't seem too superficial, as I'm relatively incompetent regarding those matters. Oh! And I hope my writing doesn't seem too formal and/or botched: since I'm not a native english speaker, I've only learnt it from books and novels.

Hopes this proves to be helpful,
Feel free to ask any question.

---

### Post by psypher on 2011-11-21
Your english is great!

I just tried that. My nautilus actually crashed as soon as I tried opening in new window. But then when I tried click home again it's all working.

hopefully it willbe fixed after reboot

---

