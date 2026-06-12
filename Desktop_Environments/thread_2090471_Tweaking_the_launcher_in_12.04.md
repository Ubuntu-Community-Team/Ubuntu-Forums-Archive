---
title: "Tweaking the launcher in 12.04"
date: 2012-12-02
forum: Desktop Environments
---

### Post by jkevinc on 2012-12-02
Hopefully a quick and simple question.  My launcher is getting crowded, and I'd like to be able to "group" applications (e.g. "system", "math", "science", etc.) and save some space. Is it possible to build a "tree-like" structure in the launcher?  [I hate to say it, but I will:  "...like the Windows "Start" menu."  Let's all pretend I didn't use that word.]

Thanks!

j. kev
Sunday, 2012.12.02 @ 1216 EST

---

### Post by LuisGMarine on 2012-12-02
I'm not sure if the unity desktop can do that, not to my knowledge at least.  What I can recommend is that you give an alternative desktop a try, the following link has a lists of the most popular ones, and how to install them.  I think Cinnamom is closer to a windows environement.  Hope this helps

[http://blog.sudobits.com/2012/05/01/alternative-desktop-environments-for-ubuntu-12-04-lts/]("http://blog.sudobits.com/2012/05/01/alternative-desktop-environments-for-ubuntu-12-04-lts/")

---

### Post by mc4man on 2012-12-03
> **jkevinc said:**
> Hopefully a quick and simple question.  My launcher is getting crowded, and I'd like to be able to "group" applications (e.g. "system", "math", "science", etc.) and save some space. Is it possible to build a "tree-like" structure in the launcher?  [I hate to say it, but I will:  "...like the Windows "Start" menu."  Let's all pretend I didn't use that word.]

Thanks!

j. kev
Sunday, 2012.12.02 @ 1216 EST

You can create a 'tree' using quicklists, just one level though.
So it's quite simple to create category icons on the launcher with a quicklist of various related apps, commands, or scripts.

I find it best to set the icon itself to run an app that is often used, plus if applicable can use the icon for drag & drop on that app.
The quicklists would launch other apps, ect.

You could look at this thread/app that probably could do this (or to some extent
[http://ubuntuforums.org/showthread.php?t=1927071&highlight=quicklists](http://ubuntuforums.org/showthread.php?t=1927071&highlight=quicklists)

or this general thread
[http://ubuntuforums.org/showthread.php?t=1962862&highlight=quicklists](http://ubuntuforums.org/showthread.php?t=1962862&highlight=quicklists)

Myself just create by making a <whatever>.desktop in ~/.local/share/applications/ & then adding to launcher.

scr. 1 is a general utility icon, scr. 2 is a multimedia icon where I've also added some crude dividers

In the case of utilities I've set the icon left click on to open synaptic, the quicklists  a combo of a couple of scripts & other apps

For multimedia the icon l. click & DnD is set to vlc

If interested in self creating just ask & can post an Ex. or 2

---

### Post by jkevinc on 2012-12-03
Got it:  I now have 32^2 * n extra pixels on the left side.  :-)
Thanks to all!

-- j. kev

---

