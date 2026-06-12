---
title: "Dark hard to read font in Panel Menu Items"
date: 2013-10-29
forum: Desktop Environments
---

### Post by LudoTW on 2013-10-29
I'm on 13.04, and some menu items in the bar menu are barely readable. Examples: in Processing, Kompozer and more.
What needs to be done?
It seems it's not a new problem but still persists. Default theme shouldn't lead to this.

 I've found a closed thread on the topic:
[http://ubuntuforums.org/showthread.php?t=1666480](http://ubuntuforums.org/showthread.php?t=1666480)
(side question: why closing a thread when the problem persists?)
And a bug report which I think is also related:
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/932274](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/932274)

Anyone has an idea on how to get normally readable bar menu items?

---

### Post by LudoTW on 2013-10-29
Solved.

So many people have this issue that it would be good to document it well, or make the defaults themes without this problem. The closed thread previously referenced to could have remained open!
Here is how I did it (at least it works in Processing and Kompozer).
```

sudo add-apt-repository ppa:shimmerproject/ppa 
sudo apt-get update 
sudo apt-get install gtk-theme-config
```
Then start the application:
Theme configuration (search for it in the Dash or install the incredibly formidable great and ultra fast Synapse).
Then here you go, change the color of the text to your liking.

References:
[http://askubuntu.com/questions/287270/how-to-change-gtk3-color-scheme-on-ubuntu-13-04](http://askubuntu.com/questions/287270/how-to-change-gtk3-color-scheme-on-ubuntu-13-04)
[http://funsurf-blog.blogspot.com/2012/09/customize-gtk-themes-with-gtk-theme.html](http://funsurf-blog.blogspot.com/2012/09/customize-gtk-themes-with-gtk-theme.html)

---

