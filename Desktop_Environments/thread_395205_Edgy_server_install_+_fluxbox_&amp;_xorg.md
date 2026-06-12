---
title: "Edgy server install + fluxbox &amp; xorg"
date: 2007-03-27
forum: Desktop Environments
---

### Post by Maelgwyn on 2007-03-27
Hey all

I've just installed 6.10 server and have aptitude updated/upgraded, then 
```
aptitude install xorg fluxbox thunar
```

However, when I try to startx or even sudo startx I get the following:

```
Fatal server error:
Caught signal 11. Server aborting

XIO: fatal IO error 104 (Connection reset by per) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.
xauth: error in locking authority file /home/haakuturi/.Xauthority
```

Any ideas on what's happening here? I'm going to try deleting .Xauthority and re-creating it....

---

### Post by kerry_s on 2007-03-27
I recommend installing gdm, ubuntu packages have gotten so tied together, that if certain things are missing you'll have problems. In your case the problem is ubuntu's new startup, it's event based, in other words no login manger, no X. I could be wrong, but i just installed gdm and moved on.

---

### Post by Maelgwyn on 2007-03-27
I hear what you're saying, but surely install xorg fluxbox & thunar count? I really don't want to have a graphical login screen...

---

### Post by kerry_s on 2007-03-27
Try running> startfluxbox

Honestly, i been where your at, but you'll end up trying to fix all the things that go wrong instead of actually using it. Installing the gdm then picking fluxbox from session and logging in is easy. With gdm you'll have a trouble free session. 
Also you can just add "1" to your boot line and it will always boot non graphical.(if i remember right :) )

---

### Post by Maelgwyn on 2007-03-27
heh ok - I'll give it another shot when I get home... I'll re-install ('cause I thought I might have more luck if I used 6.06 but NOOOOOO :P) and take things from there...

D'ya think if I installed xorg first, THEN fluxbox & thunar I'd have more luck?

---

### Post by kerry_s on 2007-03-28
I use> apt-get install xorg gdm fluxbox synaptic

when i reboot, i choose fluxbox in the session, then log in. It's important to choose the session and not use the default. Then i open synaptic, do some cleaning and then install what i want. I run a very trim system.

---

