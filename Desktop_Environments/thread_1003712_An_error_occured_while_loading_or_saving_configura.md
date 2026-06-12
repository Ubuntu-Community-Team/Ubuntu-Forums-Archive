---
title: "An error occured while loading or saving configuration information for..."
date: 2008-12-06
forum: Desktop Environments
---

### Post by prshah on 2008-12-06
Hello,

I recently ran into a HDD problem (device power supply failed while system was running) which caused the above mentioned error. 

It took out my entire desktop configuration. (See screenshot).

I was able to get it back into a working state by removing the following directories
[indent].gnome
.gnome2
.gnome_private
.gnome2_private
.gconf
.gconfd
[/indent]

However, now the system has become _extremely_ slow in this login. Other user's login in the same computer works fine.

For example, my previous glxgears performance ([from this thread]("http://ubuntuforums.org/showpost.php?p=5110661&postcount=1"))> ```
Wed Jun 04 10:36:18 ~:$ glxgears
7844 frames in 5.0 seconds = 1568.666 FPS
8661 frames in 5.0 seconds = 1732.034 FPS
8609 frames in 5.0 seconds = 1721.759 FPS
8658 frames in 5.0 seconds = 1731.450 FPS
8652 frames in 5.0 seconds = 1730.290 FPS
8599 frames in 5.0 seconds = 1719.706 FPS

```

and now```
Sat Dec 06 23:14:12 ~:$ glxgears 
2832 frames in 5.0 seconds = 566.346 FPS
3338 frames in 5.0 seconds = 667.534 FPS
3184 frames in 5.0 seconds = 636.712 FPS
3455 frames in 5.0 seconds = 690.922 FPS
3286 frames in 5.0 seconds = 655.372 FPS

```

...but it's fine in other logins.

Also, there is a substantial delay when launching programs, such as Terminal, Nautilus and Firefox. (But not for other logins). Launching the programs from a terminal does not give any output at all (in the terminal).

I've already checked for and ruled out hdd damage.

I _think_ it's probably related to some missing gconf information.

I am mainly facing sluggishness in video / display operations. I'm using an Intel 945 integrated graphics controller.

Can anyone suggest how I can "fix" this?

Thanks in advance...

---

