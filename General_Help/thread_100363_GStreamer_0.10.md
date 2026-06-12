---
title: "GStreamer 0.10"
date: 2005-12-07
forum: General Help
---

### Post by abou on 2005-12-07
I know a lot of us have been having problems with GStreamer v 0.8, but the developers just released 0.10: [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

Any chance of seeing this ported to the repositories?

---

### Post by 23meg on 2005-12-07
There's already a backport request for it. Perhaps it can be backported once it's in Dapper.

[http://ubuntuforums.org/showthread.php?t=100276](http://ubuntuforums.org/showthread.php?t=100276)

---

### Post by abou on 2005-12-07
Oh, but I want it now. [/cry]

---

### Post by poptones on 2005-12-07
There wasn't much to building it when I did it last week. Why not take this opportunity to learn how to run a configure/make?

I just switched to breezy last night so I'm busy now patching back in all the stuff I lost in the move. I'm on dialup and the deb archive I had buiolt all these months is full of hoary packages, so it takes a LONG time to run updates and such...

---

### Post by doclivingston on 2005-12-07
As mentioned in other threads, you will also need to upgrade your applications to use gstreamer 0.10.

Totem - cvs
Banshee - 0.10.0 has partial support (playback only)
Rhythmbox - cvs + patch (which will be in cvs in a few days)

---

### Post by kanem on 2005-12-09
[QUOTE=doclivingston]As mentioned in other threads, you will also need to upgrade your applications to use gstreamer 0.10.[/QUOTE]
Do you or anyone else know if upgrading gstreamer to 0.10 will break those apps that still rely on 0.8? There's only one app that I care about enough to upgrade to use 0.10. I don't even know how many other apps use gstreamer, let alone care enough to upgrade them between Ubuntu releases.

thanks

---

### Post by magnusbb on 2005-12-09
Logically, yes. I think so.

---

### Post by doclivingston on 2005-12-09
[QUOTE=kanem]Do you or anyone else know if upgrading gstreamer to 0.10 will break those apps that still rely on 0.8? There's only one app that I care about enough to upgrade to use 0.10. I don't even know how many other apps use gstreamer, let alone care enough to upgrade them between Ubuntu releases.[/QUOTE]

Major GStreamer version are *parallel installable*, which means that you can have both 0.8 and 0.10 installed at once - letting your not-upgraded applications use 0.8, and your upgraded ones use 0.10. This is really nice, because it means that you don't have to decide when to switch.

---

