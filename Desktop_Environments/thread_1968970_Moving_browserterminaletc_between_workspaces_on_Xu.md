---
title: "Moving browser/terminal/etc between workspaces on Xubuntu"
date: 2012-04-29
forum: Desktop Environments
---

### Post by GammaPoint on 2012-04-29
Hi, 

I've recently installed Xubuntu 12.04 and have compiz running. I have 4 workspaces and usually I'm able to move browsers,terminals, etc. between workspaces by using Ctrl+Shift+Alt and left or right arrow. However, this doesn't work for me anymore. It seems like the, e.g., terminal tries to switch between the two but but it never actually goes there. 

Is anyone else seeing similar problems. I've also got a dual-monitor setup (really a TV plus a monitor), although I don't know if that's related to the problem or not. 

Thanks for the help!

---

### Post by Rodney9 on 2012-04-29
Go to Settings - Settings Manager - Window Manager - Keyboard Tab

You can see the shortcuts there, basically ALT/CONTROL KP 1 , 2 etc

See screenshot

Rodney

---

### Post by GammaPoint on 2012-04-29
Hi Rodney,

Thanks for the reply. I actually see nothing if I go to the same manager (see screenshot- [http://tinypic.com/r/2mdzko/6](http://tinypic.com/r/2mdzko/6)). Maybe this has something to do with me using Compiz?

Anyway, the window I am moving starts and appears to start moving with the cube rotation when I do Ctrl+Alt+Shift, but then never makes it the complete way there, which makes me think it's a bug OR perhaps I have another conflicting setting which is breaking it.

---

### Post by GammaPoint on 2012-04-29
My bug might also be related to this one ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/874862](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/874862)). This one relates to flashing upon cube rotation, which is also something I see.

Edit: Yes, indeed. This bug was reported by another user here: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/876198).

---

### Post by GammaPoint on 2012-04-29
I've been following a bunch of links regarding this bug and apparently it might be getting fixed in an update soon. There's also a patch in this thread but I think I'm going to wait and hope that it gets fixed officially. 

[http://ubuntuforums.org/showthread.php?t=1938942&page=2](http://ubuntuforums.org/showthread.php?t=1938942&page=2)

In the meantime I'll just deal with it.

---

### Post by dentaku65 on 2012-04-30
Hi GammaPoint,

if you use compiz, you must disable "Lazy Positioning" in order to move the windows between workspaces.

See [http://ubuntuforums.org/showpost.php?p=11872229&postcount=11](http://ubuntuforums.org/showpost.php?p=11872229&postcount=11)

by

---

### Post by GammaPoint on 2012-04-30
> **dentaku65 said:**
> Hi GammaPoint,

if you use compiz, you must disable "Lazy Positioning" in order to move the windows between workspaces.

See [http://ubuntuforums.org/showpost.php?p=11872229&postcount=11](http://ubuntuforums.org/showpost.php?p=11872229&postcount=11)

by

Hi dentaku, 

Thank you for the suggestion. If it doesn't get fixed soon along with the other Compiz problems I will likely do as you suggest.

Best,
GP

---

