---
title: "terminal window size"
date: 2010-10-03
forum: Desktop Environments
---

### Post by holiday on 2010-10-03
In 10.4 I had set my default terminal size to my screen width - I type some long commands. 

After running an update this morning, my terminal comes up in the install default size. Using the preferences dialog, I cannot find the control to set the default width.

Has it been removed? I hope I'm looking in the wrong place, but I have a chilling feeling that it's been dropped or perhaps just accidentally commented out.

---

### Post by -Robert- on 2010-10-03
Just edit the command of the launcher:

```
gnome-terminal --geometry=1440x900
```You can change the last part of the command and put your preferred size in it.

---

### Post by holiday on 2010-10-03
> **-Robert- said:**
> Just edit the command of the launcher:

```
gnome-terminal --geometry=1440x900
```You can change the last part of the command and put your preferred size in it.

Thank you.

---

