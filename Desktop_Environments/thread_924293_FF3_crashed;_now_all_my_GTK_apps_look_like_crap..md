---
title: "FF3 crashed; now all my GTK apps look like crap."
date: 2008-09-19
forum: Desktop Environments
---

### Post by diamond on 2008-09-19
I'm running firefox 3.0.1 on Kubuntu 8.04, and a few days ago it crashed on me. No big deal; this happens sometimes. However, when I started it up again, I noticed that it looked dramatically different. Gone were the smooth, elegant curves of tabs, buttons and scrollbars, replaced with this:

[IMG]http://farm4.static.flickr.com/3093/2870595192_729c39ec6f_o.png[/IMG]

After some experimenting, I've discovered that this seems to be the case for *all* of my GTK apps -- GTKPod, Synaptic, GIMP, etc. They all have the same ugly, blocky, square widgets. My native QT apps, like Amarok, look just fine. Only the GTK apps are affected.

I don't know a whole lot about how KDE displays GTK widgets, but apparently something is hosed. I've tried reinstalling the KDE, QT and QTCurve libraries, and, of course, restarted multiple times, but no luck.

This is a minor thing, but it's still irritating. Anybody have any suggestions? Are there any configuration files I should look at (or delete entirely)? Thanks for any help you can offer.

UPDATE: Never mind. Solved it!

I don't know how this happened, but my .gtkrc-2.0 and .gtkrc-2.0-kde files got changed. They both have an include statement in them:

```

include "/usr/share/themes/QtCurve/gtk-2.0/gtkrc"

```

That had somehow been changed to:

```

include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

```

And the path /usr/share/themes/Qt doesn't exist on my machine. I changed it back, and everything looks good.

So it's still a bit of a mystery how this could have happened. But at least it's fixed.

---

### Post by Daisuke_Aramaki on 2008-09-19
> **diamond said:**
> I'm running firefox 3.0.1 on Kubuntu 8.04, and a few days ago it crashed on me. No big deal; this happens sometimes. However, when I started it up again, I noticed that it looked dramatically different. Gone were the smooth, elegant curves of tabs, buttons and scrollbars, replaced with this:

[IMG]http://farm4.static.flickr.com/3093/2870595192_729c39ec6f_o.png[/IMG]

After some experimenting, I've discovered that this seems to be the case for *all* of my GTK apps -- GTKPod, Synaptic, GIMP, etc. They all have the same ugly, blocky, square widgets. My native QT apps, like Amarok, look just fine. Only the GTK apps are affected.

I don't know a whole lot about how KDE displays GTK widgets, but apparently something is hosed. I've tried reinstalling the KDE, QT and QTCurve libraries, and, of course, restarted multiple times, but no luck.

This is a minor thing, but it's still irritating. Anybody have any suggestions? Are there any configuration files I should look at (or delete entirely)? Thanks for any help you can offer.

there are a lot of threads regarding the issue. there is a solution. assuming ur on kde version 3.5 variant. there was a gtk-qt-engine update a couple of days ago that was directed at kde4.1 users, but that replaces the engine that was in use earlier to draw gtk apps using kde style in kde3.5. all u need to do is fire up synaptic, and then search for gtk-qt-engine. then click on the package, and go to tab Package->Force Version and u will get an option to choose the previous packge. and then install again. the settings shud be back to normal again!

---

### Post by Daisuke_Aramaki on 2008-09-19
my bad! i didn't see the UPDATE part of ur post! sorry about that!

---

### Post by diamond on 2008-09-19
> **Daisuke_Aramaki said:**
> my bad! i didn't see the UPDATE part of ur post! sorry about that!

No problem. I appreciate the reply.

---

