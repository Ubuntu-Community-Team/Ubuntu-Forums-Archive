---
title: "some key combos unstable, seemingly too sticky?"
date: 2007-11-03
forum: Desktop Environments
---

### Post by riverfr0zen on 2007-11-03
some key combos on my Gutsy desktop seem a little unstable - almost sticky - when i do certain combinations  - for e.g. Alt-Tab to switch applications, or Ctrl-T in firefox to open a new tab, it occassionally behaves as though i haven't let go - and just keeps switching apps, or opens, like 200 tabs in firefox.

it happens infrequently, but enough to be really annoying - especially with firefox. i don't think its a hardware issue, since i've tried two desktops, and the problem doesn't happen if i boot into Windows. 

would appreciate any pointers on troubleshooting/fixing this. thanks.

---

### Post by bingoUV on 2007-11-03
I assume you are running gutsy, gnome desktop. If so, in system menu, open keyboard submenu and choose keyboard. Here, uncheck "Key presses repeat when the key is held down". See whether this solves your problem. If it does, check it again and try tweaking the settings of key auto repeat (there will be drag bars on the same window for this purpose).

If you do not find the above menu item, do the following in a terminal: 
```

xset -r 

```

This is the equivalent of unchecking "Key presses repeat when the key is held down". If you do not like this, enable auto repeat again by
```

xset +r 

```

---

### Post by spamgoat on 2007-11-06
This seems to be the same bug as described by me [here]("http://ubuntuforums.org/showthread.php?t=599978"), Perhaps we should create a "superthread" to figure out what exactly is causing this bug, and more importantly how to fix it. :)

---

