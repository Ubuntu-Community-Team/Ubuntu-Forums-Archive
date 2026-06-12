---
title: "firefox window decorations problem with nvidia"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by srturner47 on 2007-10-21
After install 7.10, everything is working pretty well.  But, I do have one problem.  The windows decorations (close, max/min, and dock buttons) partially disappear in firefox sometimes.  When this happens the top bar of firefox is always grey.  The close button disappears altogether, and half of the max/min button disappears.  Mousing over these buttons fixes the problem, but it is still a little annoying to have to do this all the time.

Any ideas on what might be causing this?  I am running with an nvidia 6200 card.  I have desktop effects on custom ---  I added cube and a couple other little things.

Thanks!

---

### Post by pjbgravely on 2007-10-21
I have a Geforce 5200 fx, and am having the same problem occasionally. I also have a problem with no windows decorations ever in the second screen. If I find a solution I will tell you, maybe that will help you.

Paul

---

### Post by pjbgravely on 2007-10-21
I fixed the problem with.

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

Then kill x

Still no decorations on the second monitor, but the first one is working well.

Paul

---

### Post by srturner47 on 2007-10-22
Great!  But, before I try that, does anyone know how to undo this if I have problems?  Nvidia says to enable this at your own risk, so I'd like to know I can get it back to normal if it messes something up.

BTW, I don't have a second monitor, so I haven't had the other issue.

Thanks!

---

### Post by pjbgravely on 2007-10-22
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.good
```

If something goes wrong fix by :

```
sudo mv /etc/X11/xorg.conf.good /etc/X11/xorg.conf
```

---

### Post by srturner47 on 2007-10-23
Hmmm..  Didn't seem to fix it.  Same problem.  :(

---

### Post by pjbgravely on 2007-10-28
It looks like a bug is your problem. [http://ubuntuforums.org/showthread.php?t=581865]("http://ubuntuforums.org/showthread.php?t=581865")

After redoing X tring to fix my dual screen the problem came back on the screen the window decorations actually worked. Compiz-Fusion is a regression so I have turned it off until they fix it. Changing window decorations may help.

Paul

---

