---
title: "Home Folder all of a sudden in Desktop"
date: 2010-10-11
forum: Desktop Environments
---

### Post by bobbykleinveld on 2010-10-11
Hi,

I'm relatively new to Ubuntu and update to 10.10 just yesterday. The problem I found is that after I restarted my computer, all the contents in my home folder are now visible on my desktop as well as the home folder itself... I tried copying them back to the home folder but got the message saying: 

"Cannot move file within itself"

My question is how to remove these files back to their original place so that I have nothing on my desktop.

Thank you in advance,

Bobby Kleinveld

---

### Post by Frogs Hair on 2010-10-11
I'm curious too , on 9.10 I dragged my home folder into my desktop icon in nautilus and had to reinstall. I was unable to separate the two . I hope there is a solution .

---

### Post by mcduck on 2010-10-12
First, hit Alt-F2 and run "gconf-editor". Use that to browse to apps/nautilus/preferences and make sure "desktop_is_home_dir" is unselected.

If that isn't enough to solve your problem, check the *~/.config/user-dirs.dirs* -file. It should have the following line somewhere:

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

This usually happens if you at some point are logged in as user, while there is no Desktop dir in that user's home. Gnome assumes that since the Desktop dir doesn't exist, you want to use your home as your desktop. After you create the Desktop dir (or finish copying back your backup, configure mounting of your home from separate partition or whatever) the settings aren't automatically adjusted to use the new Desktop directory, so you'll have to do it yourself.

---

