---
title: "nautilus, show desktop = false, does not work"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by Thorning on 2008-01-28
My problem came during some experimentation with desktop cube and multiple backgrounds.
I read about the somewhat rough solution of disabling nautilus drawing of the desktop, thus enabling the desktop cube's selected images to appear instead.

However after changing the "show desktop" option with gconf-editor nautilus still shows the desktop. I have restarted nautilus, gnome, the system and the computer and changed the option back and fourth.

sudo killall nautilus, restarts the application (?)

---

### Post by BuntuFreak on 2008-01-28
Actually this solution works for me all right. But as was explained on another thread, desktop icons do not show. If that's important to you, then you shouldn't try it.

Here's a link that will explain how to do things using gconf-editor.

[http://n00buntu.blogspot.com/2007/11/step-3-finishing-touches.html]("http://n00buntu.blogspot.com/2007/11/step-3-finishing-touches.html")

For me I immediately saw my desktop background change as soon as I closed gconf-editor. Then when I tried to change desktop, I saw a lag. It was too slow. Until I realized, there was some "caching" going on. As soon as I had visited each of my 4 desktops once, the cube rotation is now smooth.

Also, as was mentioned on another thread, my nautilus is not running at 90%. Everything seems hunky dory. Except that maybe my machine is running a little slower. Hard to tell, really. Maybe I'm imagining it because I am expecting problems, perhaps?

Anyways, I'm going to give it a few days to see how things work. I don't care about icons on desktop. I hate that in Windows too and like to keep my desktop clean.

So far so good.

---

### Post by BuntuFreak on 2008-01-28
Okay, now I'm sure. When I alt + tab or windows + tab, the graphics is not as smooth as it was before. But then again, I'm running Ubuntu on an 8 year old Dell, PIII 800 Mhz, with 512 MB RAM. And while I could have a much worse graphic card than my NVidia Mad Dog 4000, I'm sure most people are running much better hardware.

Needless to say, it is almost impossible to replicate someone else's installation because there are so many things that can go wrong. I must say I have been luckier than most in getting all my Compiz stuff working to my satisfaction. I can now go on to bigger and better things in Ubuntu.

Best.

---

