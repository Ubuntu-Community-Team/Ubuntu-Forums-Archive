---
title: "sudo application can not apply my custom theme?"
date: 2007-06-07
forum: Desktop Environments
---

### Post by hantsy on 2007-06-07
Some application need me input password, Such as "Users and Groups".
After I do that , the application Theme go back the ugly gnome default.But in Fedora , It works well.
How can keep my theme on the application that need password input?

---

### Post by tbroderick on 2007-06-08
You need to set the theme as sudo. You can run gnome-theme-manager as gksu from a terminal.

---

### Post by mcduck on 2007-06-08
The easiest way is to create symbolic links from your theme directories into root's:

```
sudo ln -s /home/<YOUR USERNAME>/.themes /root/.themes
sudo ln -s /home/<YOUR USERNAME>/.icons /root/.icons
```

After that applications running as root will always have the same theme you are using.

---

