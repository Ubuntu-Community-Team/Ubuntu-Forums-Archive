---
title: "Why aren't manpages displaying properly in mrxvt?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by jayemef on 2006-07-05
I've searched around, but can't find an answer to this. Certain characters (apostrophes, dashes, etc.) aren't displaying properly in mrxvt -- at least not in manpages. Is this a font or character set problem? I can't imagine that it's a limitation of the rxvt family. If anyone knows how to solve this, I'd be much obliged.

Screenshots attached for an example. The first is gnome-terminal, and the second mrxvt.

---

### Post by taurus on 2006-07-05
Maybe there is a problem with unicode in mrxvt!

---

### Post by jayemef on 2006-07-05
Interesting. I had been testing this with rxvt as well, which displayed the same issues. But I just saw that there is a rxvt-unicode package. After installing it, rxvt now works properly. So you are probably on the right track.


Edit: Fixed! I took a look through the mrxvt FAQ again, and saw that it does not currently support UTF-8 encoding. As a workaround, they suggest using zh_CN.GB2312, which can be done with
```
$ echo "export LC_CTYPE=zh_CN.GB2312" >> ~/.bashrc
$ . .bashrc
```

Problem solved. Thanks for the help.

---

