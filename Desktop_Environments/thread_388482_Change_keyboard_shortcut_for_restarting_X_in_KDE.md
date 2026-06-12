---
title: "Change keyboard shortcut for restarting X in KDE"
date: 2007-03-19
forum: Desktop Environments
---

### Post by eaglesfan17 on 2007-03-19
How do I change the keyboard shortcut for restarting X in KDE?

I'm running Kubuntu edgy eft and it's annoying to be typing and then forget to let off of shift and press backspace and it restarts X.

For some reason the keyboard shortcut Shift+Backspace restarts X but I want to change that to ctrl+alt+backspace

I've looked all over in KDE's shortcut menus and KDE control center but I can't find it! 

Anyone know what I should try?

---

### Post by eaglesfan17 on 2007-03-19
Wow, this forum moves fast - I tried searching around but came to no avail. Does anyone know where these shortcuts are stored? Surely they are stored in a configuration file somewhere. I'm not a pro at linux but I have found that damn near everything is fully customizable.

---

### Post by Mrwasab1 on 2007-03-19
Try adding this in an executable file in **/usr/local/bin** then place it in the session's startup



```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

That should stop shift + backpace from annoying you.

When i was reading around about this, i read a lot of people saying this was a "feature" while others say its a "bug" 
call it what you want, i just know its damn annoying when you are writing a document you havent saved for a few pages and X restarts...

---

