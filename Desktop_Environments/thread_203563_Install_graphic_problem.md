---
title: "Install graphic problem"
date: 2006-06-25
forum: Desktop Environments
---

### Post by jdm2 on 2006-06-25
I have just installed the new version of ubuntu and it installed perfect but when I start it up it just does a terminal mode run instead of a graphic one.  How can I fix this?  Thanks

---

### Post by interurban on 2006-06-25
Try typing ```
startx
``` in the terminal and hit enter, if it is reported as already running hit ctrl+alt+F7, that should switch you to the gui.

---

### Post by hbweb500 on 2006-06-25
If the Xserver does not start after typing "startx", then there may be a problem with the configuration. 

Try:
```
sudo dpkg-reconfigure xserver-xorg
```

That will open up the configuration program for your graphics setup. Once you are through with that, try "startx" again to see if it worked.

You could also try:
```
sudo X -configure
```

followed by a:
```
sudo X -config /path/to/xorg.conf.new
```
Of course, the path to your new xorg.conf will be pasted on the screen right after you run "X -configure", so make sure to use that instead of /path/to

If that works, you will need to copy that new config file to /etc/X11/xorg.conf:

```
sudo cp /path/to/xorg.conf.new /etc/X11/xorg.conf
```

Good luck! I always receive these errors when starting my desktops computer after the installation.

---

### Post by jdm2 on 2006-06-25
When I tried these commands like startx it says command unknown.  Any ideas an d when I installed 5.10 it runs but when start it up it freexes on hotplug subsystem.  Thanks

---

