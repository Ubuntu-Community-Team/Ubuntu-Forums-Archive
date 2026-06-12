---
title: "possible to change GNOME unity GUI?"
date: 2012-10-20
forum: Desktop Environments
---

### Post by Nebelhom on 2012-10-20
Hi,

about 2 months ago, I finally did the upgrade from Ubuntu lucid to Ubuntu 12.04 Precise with its spiffy, new Unity GUI.

Unforunately, after trying to get to grips with it and trying to keep an open mind, after said 2 months, I still really, reeeeally dislike it. There are so many things that just make me want to bite my desk in frustration. But this isn't a bashing thread, far from it. I am sure the designers put a lot of good work into it, it just isn't for me. :(

Now the question: Is there a good way to switch back to the old gui? Will this still be supported?

or alternatively, is it unproblematic to switch to e.g. KDE? Is it possible to run into trouble with other software already installed?

Thanks a lot for your time and help.

---

### Post by zombifier25 on 2012-10-20
The classic desktop is still available. Install gnome-panel.
Also, you can try out KDE, Xfce, LXDE, etc. Just install plasma-desktop, xfce4, lxde-core respectively. Generally you should not run into any trouble.

---

### Post by newb85 on 2012-10-20
> **zombifier25 said:**
> The classic desktop is still available. Install gnome-panel.

Umm...I don't think just installing gnome-panel is enough.  Install gnome-session-fallback.

```
sudo apt-get install gnome-session-fallback
```

Also, please note that Unity and Gnome are not the same thing.  Pre-Natty, Ubuntu came with Gnome by default.  (Gnome 2, to be exact.)  Natty-forward, it comes with Unity instead.

Of course, the current version of Gnome (Gnome 3) is very different from the "classic desktop", and you might like it.

```
sudo apt-get install --no-install-recommends gnome
```

The --no-install-recommends will prevent it from automatically installing extra gnome apps that aren't really part of the desktop environment, like evolution, gnumeric, abiword, etc.

---

### Post by sandyd on 2012-10-21
**moved to desktop environments**

---

### Post by coffeecat on 2012-10-21
> **newb85 said:**
> Umm...I don't think just installing gnome-panel is enough.  Install gnome-session-fallback.

FYI, it's the other way round for 12.04:

[http://ubuntuforums.org/showpost.php?p=11923589&postcount=4](http://ubuntuforums.org/showpost.php?p=11923589&postcount=4)

gnome-session-fallback for 11.10 and gnome-panel for 12.04, which includes dependencies that are not pulled in by gnome-session-fallback.

---

### Post by claracc on 2012-10-21
> **newb85 said:**
> Umm...I don't think just installing gnome-panel is enough.  Install gnome-session-fallback.
.

It is the same, installing gnome-panel is enough and simpler.

Here you have an excellent thread [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) to install and configure your gnome classic without effects desktop, similar to the gnome 2 one and supported by ubuntu.

---

### Post by Nebelhom on 2012-10-21
Hey thanks for all your replies.

This leaves me with one last question that is in the same vein:

You guys mentioned gnome-panel etc., but zombifier25 also mentioned KDE, Xfce, LXDE, etc.

Now, is the gnome-panel classic desktop a "lasting" option or is it likely to be abandoned any time soon with no support? Obviously I ask this, so that I don't install this and half a year down the line need to look for a new option yet again.

Thanks a lot again.

@sandyd: Thanks for moving it. I don't post here particularly often and thought it fit best in the beginner's questions (because that's what I am with regards to ubuntu)

@all: After all your answers I realised that my initial question has been asked before. I apologise for this, but it would appear that I didn't use (or know) the correct search keywords (such as "classic gnome") and only found threads with ways to tweak the existing gui

---------------------------------

*sigh of relief* Having followed the advice above, in particular thread [http://ubuntuforums.org/showthread.php?t=1966370]("http://ubuntuforums.org/showthread.php?t=1966370"), I was able to revert back to the original view without problems.

This is almost like when I was 15 years old and still living at home. One day, I would come back and my mother rearranged all the furniture in my room, because she felt like it. Thankfully, there is a happy ending this time :D

---

### Post by cmcanulty on 2012-10-21
well if you use 12.04 classic as I do it has support for 5 years so a long time before you have to worry about it disappearing

---

### Post by Nebelhom on 2012-10-21
@cmcanulty: Thanks for the info. That is indeed still a bit off :)

Cheers!

---

### Post by dandaman96 on 2012-10-21
I was in the same boat as you when I upgraded to 12.04.  I loved Gnome2 and had been using it for years.  I eventually made my way over to Gnome3 and with some modification, I find I now prefer it over the previous Gnome.  I still have a pseudo-Gnome2 options available by loging into Gnome Classic.  

Check out the following page and look under the "Gnome" section.  It describes how to make Gnome3 usable.
  
[http://www.foxswap.com/computers-and-technology/how-to-fix-ubuntu-12-04/](http://www.foxswap.com/computers-and-technology/how-to-fix-ubuntu-12-04/)

---

