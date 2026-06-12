---
title: "Best Mac Os x Like dock"
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by jazzman84116 on 2007-06-07
What is the Most stable one and user friendly one to install  I tried the avant windows manger but it really messed up.

---

### Post by Kobalt on 2007-06-07
To me AWN is the closest one...

---

### Post by notwen on 2007-06-07
For usability/stability I'd recommend AWN, although for the look and feel of OSX's dock, you may want to look into KXdocker(may or may not be for KDE only).  Good luck.

---

### Post by reclusivemonkey on 2007-06-07
Did you install it yourself or did you use the one in the repo? I've not had any problems with this one. Try adding this to your /etc/apt/sources.list;

```

# Avant Window Navigator
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator

```

---

### Post by russbuss on 2007-06-08
I also vote for Avant Window Navigator.

I have tried gnome-dock, kiba-dock, and kxdocker, and AWN is by far the easiest to use and most stable.  Kiba-dock is nice, but it is still a bit buggy.  Additionally, AWN supports svg and png icons, whereas kiba-dock only seems to accept pngs.

Anyhow, as has been mentioned previously, you should not install AWN from the repos.  The fellow who maintains AWN even admits as much.  I got AWN to work on Feisty by following the instructions on the first page of this HowTo:

[http://ubuntuforums.org/showthread.php?t=385981&highlight=avant](http://ubuntuforums.org/showthread.php?t=385981&highlight=avant)

One caveat: This requires you to check-out the latest version from SVN.  Since I am an idiot I didn't know what SVN stood for when I started this whole process.  In case you are like me, it stands for Subversion which you need to install from Synaptic if you haven't already.  Without it, the following line of code from the HowTo won't work:

```
svn checkout http://avant-window-navigator.googlecode.com/svn/trunk/ avant-window-navigator
```

Anyhow, hope this helps.

And remember that you **MUST have a compositor running** (i.e. Compiz or Beryl) or else AWN will show up with an ugly black box around it.  There are about 20 posts in the HowTo above from folks asking about the black box.......

---

### Post by dannymichel on 2007-06-12
AWN acts NOTHING like the mac dock.
What's the dock in [this first video]("http://www.ny-dev.com/forums/f215/ubuntu-beryl-1499/")?

---

### Post by eitan_a on 2007-06-12
that's kiba-dock

---

### Post by russbuss on 2007-06-13
> **dannymichel said:**
> AWN acts NOTHING like the mac dock.


What aspects of the mac dock do you think AWN is missing?

It allows you to add application launchers to the dock.  It represents instances of open applications (launched from the dock or otherwise) to the right of a separator bar in the dock.  It even includes arrowheads to indicate which of the application launchers is running an open application.

One thing that it is missing is the ability to add links to the trash and support for other gnome panels.

It is true that kiba-dock does support these features, but, from my experience, it is still buggy.  While the trash works fine, I never got the window lists to work properly.  This doesn't mean it won't ever be better than AWN, but I would say that, currently,  AWN is the most stable dock with the best collection of mac-like features.

---

### Post by shazm on 2007-06-13
the difference between kiba dock and awn is, that kiba is a launcher with stylish effects and awn is a replace for Gnome's panel, where you see which process is currently running.

---

