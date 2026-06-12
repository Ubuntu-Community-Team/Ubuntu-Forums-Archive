---
title: "Gnome-Panel Does Not Start"
date: 2010-10-23
forum: Desktop Environments
---

### Post by Shadow21 on 2010-10-23
For some reason when I start Ubuntu on my Netbook the Gnome-Panel does not start. It was working perfectly fine until I turned on Ubuntu one day and it didn't start up. I didn't mess with anything that would make it not start up so I don't know what's wrong.

I can pull up the Terminal (using ctrl+alt+t) and type "gnome-panel" and it'll come up but when I close the terminal the panel will also close.

How can I make the Gnome-Panel start up when the computer starts?

---

### Post by elvissims on 2010-10-23
I did a new install on a friends machine this week with the same problem.  This seemed to work.

Ctl-Alt-T to pull up terminal.
Type gnome-panel and hit enter.
With your panel running, select System->Preferences->Startup Applications.
Click Add and in the "Command:" line add gnome-panel and click Add.
Click Close.

I hope that works for you.  It seems to work for me.

---

### Post by flxdms on 2010-10-23
Try 

```
nohup gnome-panel
```

and once you've done that, close the terminal and do what elvissims said.

---

