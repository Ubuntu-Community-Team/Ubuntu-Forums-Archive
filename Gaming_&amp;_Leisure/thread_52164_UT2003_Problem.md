---
title: "UT2003 Problem"
date: 2005-07-26
forum: Gaming &amp; Leisure
---

### Post by Zerboxx on 2005-07-26
I've seen similar problems, but I can't seem to find a fix for this.  I installed ut2003 with the linux installer (no problems), I've killall esd'd so sound should be fine, but here's my problem:
```
jon@lappy486:~/ut2003$ sh ut2003
fcntl: Operation not permitted
fcntl: Operation not permitted
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
OpenGL renderer relies on DXTC/S3TC support.

History:

Exiting due to error
```
Any help on this would be greatly appreciated!

---

### Post by shawn on 2005-07-27
Im sorry but I don't think you will get it working with your graphics card. See here:

[http://www.linuxquestions.org/questions/history/36440](http://www.linuxquestions.org/questions/history/36440)

---

### Post by Zerboxx on 2005-07-27
[QUOTE=shawn]Im sorry but I don't think you will get it working with your graphics card. See here:

[http://www.linuxquestions.org/questions/history/36440](http://www.linuxquestions.org/questions/history/36440)[/QUOTE]
Thanks shawn, but is it my graphics card, even if I get all hese in terminal:
```
$ cat /etc/X11/xorg.conf | grep -i driver
        Driver          "keyboard"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "ati"
```
and
```
$ glxinfo | grep -i "direct"
direct rendering: Yes
```
??

---

### Post by shawn on 2005-07-27
I'm no expert in these matters but I had a look around for you. DXTC and S3TC are something to do with texture compression and it seems that your gfx card does not support them or does not have them enabled. What is your gfx card?

---

### Post by RJARRRPCGP on 2005-08-02
```
fcntl: Operation not permitted
``` 

That message likely means you're required to use **sudo** !

---

