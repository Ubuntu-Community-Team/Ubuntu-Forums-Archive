---
title: "Migrating to FluxBox questions"
date: 2009-05-20
forum: Desktop Environments
---

### Post by FFighter on 2009-05-20
Hello,

I want to migrate to FluxBox in an attempt to use a lighter and less-distracting Desktop environment. I've been using Gnome all this time, and even though I like it, my experience with it in the lately has not been so good performance/resource-wise. It is feeling sluggish and I'm starting to feel burried by all its abstractions -- and this is another good point, I want to be closer to the Linux core as possible.

For example, even though I use Linux for almost 3 years, I feel kind of embrassed to ask how can I connect to a wireless network without the NetworkManager.

I installed FluxBox in 9.04 through APT, and set it as the default session. It felt very fast and much more responsive than Gnome. However, I could not figure out how to connect to my wireless network. I controverselly miss NetworkManager :S

Also, how could I set up so it connects to the network automatically (the same behavior as if I were using the NetworkManager at the startup of the system).

Another thing -- I felt that the font rendering in FluxBox was different (worst actually), how could I configure it?

So, if someone could enlighten-me here, I would be grateful :)

Thanks.

---

### Post by FFighter on 2009-05-20
*bump*

Anyone? :)

---

### Post by m_duck on 2009-05-20
For the network thing, you can still run network manager in fluxbox. Just add the following to the fluxbox autostart file (I'm not sure where it actually is):```
nm-applet --sm-disable &
```That should then run network manager when you log into fluxbox.

If network manager starts misbehaving for whatever reason, [WICD]("http://wicd.sourceforge.net/") is a very good replacement.

I don't know about the answer to your second question, but there is an article [here]("http://www.linux.org/lessons/short/fluxbox/index.html#CONFIGURE-FLUXBOX") under the title "Sprucing up fonts" which seems to relate to it?

HTH

---

### Post by Anzan on 2009-05-20
Regarding fonts and many other settings, just run

gnome-control-center &


It's "cheating", but it gets a lot of config stuff done for services that a WM doesn't handle.

---

### Post by RoboNuggie on 2009-05-21
The fonts..... I had that until I decided one day to compile Fluxbox to try and squeeze every last drop of speed.... and came across --enable-xft in the options.....

Worked for me.....

---

