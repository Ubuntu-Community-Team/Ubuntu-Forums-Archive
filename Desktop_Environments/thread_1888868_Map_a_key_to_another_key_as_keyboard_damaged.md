---
title: "Map a key to another key as keyboard damaged"
date: 2011-11-30
forum: Desktop Environments
---

### Post by esafwan on 2011-11-30
My @ or 2 key is not working. I want to set it like, if user press Alt + a or something the 2 should be inserted to the active window. I have achieved this in windows using Auto It. In ubuntu i saw some solutions but couldn't do it. Any help would be appreciated. Or else i will be forced to move back to windows :-(

---

### Post by gmargo on 2011-11-30
I don't know about using an Alt combination, but it is relatively easy to map another key to be your "2" key.

In this post I went over how to map the Menu key to another key:
[http://ubuntuforums.org/showthread.php?t=1791033&highlight=xmodmap](http://ubuntuforums.org/showthread.php?t=1791033&highlight=xmodmap)

Just change the **xmodmap** input to be:
```

keycode 135 = 2 at 2 at

```Now the Menu key (to right of space bar) is a "2" key.

Test it first with this command:
```

xmodmap -e "keycode 135 = 2 at 2 at"

```

---

