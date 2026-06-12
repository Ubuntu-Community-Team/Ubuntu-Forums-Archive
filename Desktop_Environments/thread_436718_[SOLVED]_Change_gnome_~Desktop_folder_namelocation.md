---
title: "[SOLVED] Change gnome ~/Desktop folder name/location"
date: 2007-05-08
forum: Desktop Environments
---

### Post by olejorgen on 2007-05-08
Is it possible to make gnome use a different name/location than ~/Desktop for the desktop directory?

I like to have my folder names in lowercase, so I'd like it to be named desktop, not Desktop

Yeah, I know, it's a HUGE issue for me. 
Thanks :D

---

### Post by mcduck on 2007-05-08
No it's hardcoded.

But if it really is a HUGE issue to you, you could create a file called '.hidden' inside your home directory, and type 'Desktop' inside that file to hide the existing Desktop dir. Then create a symlink called 'desktop', pointing to the actual Desktop dir. And just try to forget that the 'Desktop' still exists ;)

```
echo Desktop > .hidden
ln -s Desktop desktop
```

---

### Post by wdaniels on 2008-03-24
I was just looking for an answer to this same question and later discovered that you can now change it in the file ~/.config/user-dirs.dirs (XDG_DESKTOP_DIR variable).  See [here]("http://freedesktop.org/wiki/Software/xdg-user-dirs") for more info on this file.

---

