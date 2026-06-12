---
title: "New Ubuntu User"
date: 2005-12-20
forum: Desktop Environments
---

### Post by catlee on 2005-12-20
I just put Ubuntu on my computer and I'm slowly getting all the glitches out, Now I can't figure out how to get icons displayed on my desktop. They'll save to the folder labeled desktop but not the actual desktop. Thanks for your help.

---

### Post by Sutekh on 2005-12-21
Can you confirm the location of the "Desktop folder"

Is it in the following path?  
```

/home/<username>/Desktop/

```
It is caps sensitive too. Must be a capital D.

---

### Post by dcstar on 2005-12-21
[QUOTE=catlee]I just put Ubuntu on my computer and I'm slowly getting all the glitches out, Now I can't figure out how to get icons displayed on my desktop. They'll save to the folder labeled desktop but not the actual desktop. Thanks for your help.[/QUOTE]
What sort of icons?

If you go to the desktop, right-click and select "Create Launcher", then that should end up on the desktop.

---

### Post by Sutekh on 2005-12-21
You should also note, that there is a setting in the Configuration Editor (Applications -> System Tools -> Configuration Editor) 

Under apps -> nautilus -> preferences, there is an option called desktop_is_home_dir.  

If this is checked/enabled, then your home folder /home/<username> will be the desktop folder.  If it is unchecked, then /home/<username>/Desktop is the desktop folder.

---

