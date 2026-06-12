---
title: "Xubuntu Desktop Gone"
date: 2006-07-25
forum: Desktop Environments
---

### Post by rikdin on 2006-07-25
I installed konqueror to see what it is like, but it made my desktop disappear. I uninstalled it but thunar doesn't seem to have taken back my desktop for this user. As other users I can login and get the old thunar desktop back.

I've tried uninstalling and re-installing thunar and xubuntu-desktop packages. Because it is only for my own user, I think it must be in my . files in my home directory.

Right now the ~Desktop directory exists, I just can't see it on my desktop. And I can't drag files too and from the desktop. Any ideas as to what . file I need to delete/modify?

---

### Post by taurus on 2006-07-25
Remove ~/.config and it should be back to normal, default, again...

```

rm -rf ~/.config

```

---

### Post by rikdin on 2006-07-25
Thanks taurus, but I removed .config, logged out and logged back in and there is still no desktop! :(

---

### Post by aysiu on 2006-07-25
Alt-F2 ```
xfdesktop &
```

---

### Post by rikdin on 2006-07-26
Thanks for the help! xfdesktop needs to be running apparently!

---

