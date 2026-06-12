---
title: "Moving videos folder back to its original position on Nautilus sidebar"
date: 2018-09-14
forum: Desktop Environments
---

### Post by jbh54enwiler on 2018-09-14
I run the main flavor of Ubuntu 18.04 and somehow managed to accidentially move the sidebar for my videos folder to the lower part of my sidebar, away from the other main home subfolders like documents and music.  This caused it to lose its original icon and I can't drag it back onto the main sidebar.  It still works as a folder but I'd like to have it back where it started.  Any suggestions?

---

### Post by vanadium on 2018-09-15
First of all, delete the instance you do not want by right-clicking on it, and selecting "Delete". This removes the bookmark you added yourself at some point.

Then you can restore the "special" status of your Video folder. Open the relevant configuration file:
```

gedit ~/.config/user-dirs.dirs

```
edit the line for your Videos folder to look like
```

XDG_VIDEOS_DIR="$HOME/Videos"

```
If the line is not there, add it. If your Videos folder is not in its normal location, either place it back or update the pathname in the config file.

You may or may not need to log out then login again before you see the result.

---

