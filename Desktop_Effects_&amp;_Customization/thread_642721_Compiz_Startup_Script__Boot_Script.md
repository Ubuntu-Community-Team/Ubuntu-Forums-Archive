---
title: "Compiz Startup Script / Boot Script"
date: 2007-12-16
forum: Desktop Effects &amp; Customization
---

### Post by XFocus on 2007-12-16
Hi all,

I've got a triple screen setup on two video cards.  The two left screens are on one card, the right screen is on the second.  I've got them running on two different XScreens, Display 1 & 2 (Screen0) and Display 2 (Screen1).  When Ubuntu starts up, Compiz will be present on the two left screens, however the file menus and right click menus are sluggish.  

To fix this I need to run:

```
compiz --only-current-screen
```

After I do that I need to do the same on the third screen which boots up without any screen manager.  So basically I now have both screens running compiz and all is well.

I've been trying to figure out how to get a start up script to accomplish this but unfortunately I'm still newbish and haven't had much luck.  Right now it's more of a nuisances than anything but I'd like to automate it.

Any help is appreciated!

---

### Post by erfahren on 2007-12-17
at the very end of this post there are instructions to create that type of script with a delay, and start the script with the Sessions startup. You should be able to adapt it for your uses.
[http://ubuntuforums.org/showpost.php?p=3026765&postcount=2](http://ubuntuforums.org/showpost.php?p=3026765&postcount=2)

You don't necessarily need to put it in ~/bin , you could put the script(s) in a folder inside the ~/.config/compiz directory. (~/.config is a hidden directory in your home folder - press Ctrl+H to show them)

---

