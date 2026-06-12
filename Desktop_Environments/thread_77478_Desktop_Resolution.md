---
title: "Desktop Resolution"
date: 2005-10-16
forum: Desktop Environments
---

### Post by yamphon on 2005-10-16
After i have installed Ubuntu 5.10, my screen resolution is only 640x480, how do i get more options under the screen resolution menu?

I'm new and excited about ubuntu.

---

### Post by fimbulvetr on 2005-10-16
Go to the command line and type:

```
cat /etc/X11/xorg.conf
```

And paste it here.

---

### Post by professor_chaos on 2005-10-16
Or fix it on your own by ```
sudo dpkg-reconfigure xserver-xorg
```
making sure to check the appropriate resolutions when asked.

Although learning the format of /etc/X11/xorg.conf is very useful.

---

### Post by yamphon on 2005-10-17
Hey,

I tried going to terminal and i was unable to reconfigure either of the methods shown. I wasn't able to change the resolution. Could you go into more detail on how to get it done. i was going to terminal and typing either cmds.

:confused:

---

