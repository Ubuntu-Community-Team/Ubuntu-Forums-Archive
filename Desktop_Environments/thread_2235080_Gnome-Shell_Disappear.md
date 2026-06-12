---
title: "Gnome-Shell Disappear"
date: 2014-07-18
forum: Desktop Environments
---

### Post by filipemolina-q on 2014-07-18
Hello everyone, this is my first post.

This problem happens in random operations, but most notably when I try to download a file using Google Chrome.

The title bars of the applications, the main bar of the system, everything goes away. If I happen to have one window maximized (as is the case now), it still functional covering all the space on the screen.

I already tried to do:

```
sudo apt-get install --reinstall gnome-shell
```

But the problem persists. Another thing a tried was reset Gnome to Defaults:

```
[FONT=Ubuntu Mono]rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*[/FONT]
```

from this post [http://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults](http://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults) but it didn`t make it for me.

When I restart the computer, everything looks fine, but the problem persists.

If I hit Ctrl + Alt + F1 and go to the text mode, and insert `gnome-shell --replace` I get an error telling me that X cannot be loaded.

---

### Post by grahammechanical on 2014-07-18
What makes you think that the problem is with Gnome shell? What hardware do you have? What CPU? How much system memory (RAM)? What graphic adapter and how much of its own memory does the graphic adapter have?

And this only happens when you download a file using Chrome? In the terminal you can run this command

```
top
```

and that utility will show you what applications and services are running and what share of system resources ( percentage of CPU and memory) each are using. You might be able to see what is causing this.

On my machine I have installed system-load-indicator (also called indicator-multiload). That shows me how much the CPU is being used, and how much memory is being used and it also shows internet activity. It is useful for finding out if the problem is with the OS or the application.

Regards.

---

