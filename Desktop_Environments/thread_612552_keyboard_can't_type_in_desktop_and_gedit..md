---
title: "keyboard can't type in desktop and gedit."
date: 2007-11-14
forum: Desktop Environments
---

### Post by henryluo on 2007-11-14
Hi, all,
since I upgrade my system to 7.10 from 7.04, the keyboard can't type any thing in desktop and gedit,
but the shortcut key works fine, when I  rename a file, I can't type it, but i can ctrl+C and ctrl+V to make it..and the F1-F12 works fine,  , and in other program ( like firefox, openoffice etc) the keyboard works fine
I was wondering if you could give me some suggestion to check it. 
thank you very much.

---

### Post by eggdeng on 2007-11-14
Have you got a  keyboard layout specified in System -> Preferences -> Sessions -> Startup Programs tab? Something along the lines of ```
xmodmap /usr/local/share/xmodmap/xmodmap.us
```

---

