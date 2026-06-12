---
title: "Remove docklets"
date: 2019-07-04
forum: Desktop Environments
---

### Post by kriscoinet on 2019-07-04
Hye,
_I have clumsily create 2 docklets, right and left. They are empty and I wish to remove them. I do not know how. I do not have access to the settings.
[IMG][[IMG]https://pix.tdct.org/upload/thumb/1562264551.png[/IMG]]("https://pix.tdct.org/?img=1562264551.png")[/IMG]

_The trash is now in Docky, I'd like to remove it from the desk.

Thank you.

---

### Post by #&amp;thj^% on 2019-07-04
Run the following:
```

cd /usr/share/gnome-shell/extensions/
sudo mv ubuntu-dock@ubuntu.com{,.bak}
```
also reload session with, Use (**ALT + F2**) and type "**r**" (without quotes) in the input.
This is a nice way to go if you don't want to remove any software, i.e. you want to go back and use the vanilla dock some time in the future.

---

