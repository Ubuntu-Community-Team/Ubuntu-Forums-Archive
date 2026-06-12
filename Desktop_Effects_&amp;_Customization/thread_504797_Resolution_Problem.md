---
title: "Resolution Problem"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by ukulele_ninja on 2007-07-19
I tried lowering my resolution settings in the system>monitors section and it made everything really big and goofy...now i want my old settings back, but when i try to go in and change it, it looks all jarbled and crazy. after i restart it goes back to the lower res. what do i do??

---

### Post by ukulele_ninja on 2007-07-19
Great... Now everytime I boot its a jarbled mess...

---

### Post by dougfractal on 2007-07-19
At login screen

press [ctl]+[alt]+[f1] to goto treminal
login 
type
Code:
```

mv .gconf gconf.old
```

will move the gnome config file to a backup. Gnome settings will  become default as if a new user.



press [ctl]+[alt]+[f7] to goto graphical

---

