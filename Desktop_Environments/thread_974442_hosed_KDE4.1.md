---
title: "hosed KDE4.1"
date: 2008-11-07
forum: Desktop Environments
---

### Post by anystupidname on 2008-11-07
OK, so I'm still trying to force myself to use KDE4 in case I'll find a way to configure it to a look and feel I don't absolutely hate. So I went into themes and picked some dark theme but before I could apply it, the screen went dark. Is there a way to reset the KDE4 config so I can see what I am doing again?

Thanks!

---

### Post by dabl on 2008-11-07
You can reset it to default settings by renaming the ~/.kde folder, but you will lose custom settings when you do that.  At your home user prompt:

```
sudo mv .kde .kde_bak
```

Then Ctrl-Alt-Backspace to restart the X server and log in again.

---

