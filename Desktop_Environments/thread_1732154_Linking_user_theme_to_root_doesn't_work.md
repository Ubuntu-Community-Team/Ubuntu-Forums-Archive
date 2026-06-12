---
title: "Linking user theme to root doesn't work"
date: 2011-04-17
forum: Desktop Environments
---

### Post by l07 on 2011-04-17
I ran
```
sudo rm -R /root/.themes
sudo rm -R /root/.icons
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons

```

but on running ```
gksu nautilus
``` it still uses the same theme, not my own.
How do I fix this?

---

### Post by Copper Bezel on 2011-04-18
It's not that root's theme needs to be set to yours, it's that root can't read yours, despite being launched under your GTK theme settings as an environment variable.

Instead, copy the folder of your chosen theme from ~/.themes to /usr/share/themes. If you're using a theme that mixes and matches parts of themes you've downloaded, copy all the relevant parts. Icon themes will need to be copied from ~/.icons to /usr/share/icons, as well.

In the future, just install your new downloaded themes directly in /usr/share/themes.

---

