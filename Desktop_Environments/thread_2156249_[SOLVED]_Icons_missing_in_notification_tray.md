---
title: "[SOLVED] Icons missing in notification tray"
date: 2013-06-21
forum: Desktop Environments
---

### Post by fredbird67 on 2013-06-21
I'm working on creating my own Ubuntu-based distro, having started with Ubuntu Mini Remix as my base and building on it from there, using Xfce for my desktop.  I have never gotten the network or blueman applets to show up in the notification area, which I know for a fact IS present on the panel, because I put it there, although unless I have the power manager applet on, it currently looks like little more than an invisible separator.  Does anyone know how to get the network manager and blueman applets to appear?

Thanx in advance,
Fred in St. Louis

---

### Post by Frogs Hair on 2013-06-21
The xfce4-goodies package offers aditional applets including network monitor, weather, and othes , but I don' t know if that is what you are asking about. I use the XFCE session along with may other window managers.

---

### Post by fredbird67 on 2013-06-21
No, this isn't part of the Xfce Goodies, of that I'm sure.

---

### Post by fredbird67 on 2013-06-21
Well, guess what...I tried running "nm-applet &" and it turns out that there's an error in my GTK theme (on the GTK3 side, of course -- I wish the GNOME developers would've had the good sense to refrain from fixing something didn't need fixing in the first place) that prevents the notification area icons from showing up.  BTW, the default theme I had in mind is one I created, but I've been thinking about doing some changes to it anyways, so I think I'll focus my energies on that this evening.  Therefore, I'm gonna mark this one as solved, even though it technically isn't -- but at least I now know what to do.

---

### Post by fredbird67 on 2013-06-22
Turns out I was wrong -- dead wrong.  Even after re-creating the theme, I'm still getting this problem.  What's more, I'm running my new theme creation on a Linux Mint Xfce box, and it's working just fine, even with errors generated when starting nm-applet from the terminal.  So no, this one's NOT solved...

---

### Post by fredbird67 on 2013-06-22
OK, consider this one SOLVED.  I finally gave up on the GNOME Network Manager and replaced it with WICD -- and WICD's network icon shows up in the notification area and works without a hitch, so I think I'll go with WICD instead.  As for the bluetooth, I thought to myself "I wonder if it would work with a Bluetooth adapter plugged in?".  While I have one plugged into the back of my main desktop, I didn't wanna pull the thing out of my desk to get it, so I borrowed my wife's off her laptop and plugged it in to the computer on which I'm working on my distro.  With the system off, I plugged it in, turned it on, logged in...and there was my Bluetooth icon!  I then turned the system back off and returned it to her laptop in a MUCH better mood. :-D

---

### Post by Bert Mariën on 2013-10-21
Thanks.
After upgrading to Saucy, I lacked the network icon also.
Running "nm-applet &" fixed it.

Many thanks for your post.

---

