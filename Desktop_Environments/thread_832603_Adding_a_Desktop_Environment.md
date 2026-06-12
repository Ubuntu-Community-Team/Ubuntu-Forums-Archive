---
title: "Adding a Desktop Environment"
date: 2008-06-17
forum: Desktop Environments
---

### Post by Gannett on 2008-06-17
I've searched the forum for an answer to this but can't find anything, so sorry if I'm going over old ground.  I am using regular Ubuntu with GNOME.  My system is a Pentium 4 2.8GHz, 512Mb RAM and 1Gb swap space, with little room for expansion.  I've turned off as much of the fancy stuff in GNOME as possible and probably because of the limited memory, it's hammering the processor for little stuff.  Someone suggested using Xfce desktop to make better use of the limited system.  Is there a way I can install it on top of my current installation to see if it works?  
Many thanks.

---

### Post by jw5801 on 2008-06-17
You can install it through the package manager with ```
sudo apt-get install xfce4
```
Or you can use ```
sudo apt-get install xubuntu-desktop
```
To give yourself the same system you would have if you'd done an Xubuntu install.

With either you can access your new desktop environment by clicking on the 'sessions' button at the login screen and choosing Xfce rather than GNOME.

---

### Post by Gannett on 2008-06-17
Many thanks, I'll give it a whirl.
This really is a fantastic forum!

---

### Post by Gannett on 2008-06-18
Well, I installed Xubuntu-desktop and it worked a charm.  CPU is running lower, but not that low, but I'm not complaining.  It's nice having two desktop environments to choose from.  I'll be building a much better PC in the near future, and will install both on that too.
Many thanks, very useful bit of advice.

---

### Post by atomkarinca on 2008-06-18
> **Gannett said:**
> Well, I installed Xubuntu-desktop and it worked a charm.  CPU is running lower, but not that low, but I'm not complaining.  It's nice having two desktop environments to choose from.  I'll be building a much better PC in the near future, and will install both on that too.
Many thanks, very useful bit of advice.

If you're looking for a lightweight DE then you should definitely give Openbox a try. It's highly customizable. Sure it needs a little more work but not very hard to get used to. And if you like pretty, just have a look at [E17]("http://ubuntuforums.org/showthread.php?t=546746").

---

