---
title: "start up to X's"
date: 2005-12-07
forum: Desktop Environments
---

### Post by vtec on 2005-12-07
Is it possible to an X session on both F7 and F8. How could one go about doing this??

---

### Post by 23meg on 2005-12-07
You'd need to change the default runlevels and modify /etc/inittab accordingly I guess.

---

### Post by vtec on 2005-12-07
That is what i was thinking. I looked in inittab but only saw entries for 1-6. I still need to hunt down where X is started.

---

### Post by cwaldbieser on 2005-12-07
[QUOTE=vtec]That is what i was thinking. I looked in inittab but only saw entries for 1-6. I still need to hunt down where X is started.[/QUOTE]
I am pretty sure if you do something similar to
```

$ startx --display :1

```
It will start another X session on a free virtual terminal.

---

### Post by vtec on 2005-12-07
turns out this will do it:

```
startx -- :1
```


however that only starts a xserver and no window manager or desktop. I'll have to do some testing and find out how to start somthing i can use to open windows. All i need is a super light weight window manager so i can run one app in full screen mode and leave it there.

---

### Post by cwaldbieser on 2005-12-07
[QUOTE=vtec]turns out this will do it:

```
startx -- :1
```


however that only starts a xserver and no window manager or desktop. I'll have to do some testing and find out how to start somthing i can use to open windows. All i need is a super light weight window manager so i can run one app in full screen mode and leave it there.[/QUOTE]
Once you get the second X display Server going, put it in the background and run something like:
```

#Start xfce4 on display 1
$ xfce4-session -display :1

#Start gnome on display 1
$ env -u SESSION_MANAGER gnome-session --display :1

```

---

