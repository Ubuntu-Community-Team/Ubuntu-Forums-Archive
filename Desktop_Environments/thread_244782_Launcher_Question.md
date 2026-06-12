---
title: "Launcher Question"
date: 2006-08-26
forum: Desktop Environments
---

### Post by Georgie-o on 2006-08-26
How do you do a Desktop Launcher in Gnome if you want it to do multiple steps?  I want to make a launcher to a tn 5250 (telnet) to connect to our AS400 at work.  When I make the launcher and select "run in terminal"  it opens a terminal and runs.  However, this program is made to run best in **xterm**, not the regular gome terminal (which is what "run in terminal" uses).  So I can make a launcher for xterm, but how do I add tn5250 xxx.xx.x.x?  Thanks

---

### Post by aysiu on 2006-08-26
Have you thought of doing something like this? ```
sudo dpkg-divert --divert /usr/bin/gnome-terminal.old --rename /usr/bin/gnome-terminal
sudo ln -s /usr/bin/xterm /usr/bin/gnome-terminal
```

---

