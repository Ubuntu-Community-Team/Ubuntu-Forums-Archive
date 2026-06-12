---
title: "Confusion surrounding GNOME classic/fallback/flashback sessions"
date: 2013-11-01
forum: Desktop Environments
---

### Post by kansasnoob on 2013-11-01
Beginning with Oneiric (11.10) Ubuntu switched to using GNOME 3 as it's base with Unity as the default desktop environment using the Compiz window manager whereas GNOME themselves used the new GnomeShell DE with the Mutter window manager. 

As a "fallback mode" for hardware that wouldn't support the Compiz window manager Ubuntu offered the Unity-2D session using the Metacity window manager whereas GNOME themselves offered a "fallback" session that was presented as "GNOME Classic" or "GNOME Classic (no effects)" at login in Ubuntu if the package 'gnome-panel' was installed.

The GNOME devs had never intended to provide long term support for their "fallback session" so during Ubuntu's Raring dev cycle they sounded the death knoll for the "fallback" session, but then Edubuntu dev announced their intent to keep it alive in order to support their LTSP installs:

[http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/](http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/)

In the meanwhile the GNOME devs decided to create a new Classic session that runs on top of the Mutter window manager. It should in no way be confused with the earlier "fallback" that Ubuntu called "classic" though. You can get a glimpse of the new "Classic" here:

[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)

In order to make the new Gnome Classic mode distinguishable from the the older "classic" mode during the Raring dev cycle the name "classic" was replaced with "fallback", then in Saucy the name was changed from "fallback" to "flashback".

End of history lesson.

Now let's do a recap:

In Ubuntu & Edubuntu Oneiric, Precise, and Quantal if you installed the package 'gnome-panel' you'd then find the additional login options "GNOME Classic" and "GNOME Classic (no effects)". The standard "Classic" session uses the Compiz window manager whereas the "(no effects)" session uses the Metacity window manager.

In Ubuntu, Edubuntu, and Ubuntu GNOME Raring once the package 'gnome-panel' is installed you'll then find the additional login options "GNOME Fallback" and "GNOME Fallback (no effects)". The standard "Fallback" session uses the Compiz window manager whereas the "(no effects)" session uses the Metacity window manager.

In Ubuntu GNOME Saucy you will find a new "GNOME Classic" session when you login without adding any additional packages, but this session is in no way related to the earlier classic or fallback sessions! The new GNOME Classic session runs on top of the Mutter window manager and could perhaps be best described as a 'gnome-shell' session using a popular collection of GNOME Shell Extensions.

In Ubuntu, Edubuntu, and Ubuntu GNOME Saucy once the package 'gnome-panel' is installed you'll then find the additional login options "GNOME Flashback" and "GNOME Flashback (no effects)". The standard "Flashback" session uses the Compiz window manager whereas the "(no effects)" session uses the Metacity window manager.

---

### Post by grahammechanical on 2013-11-01
Is it factually correct?

Well, I would say that the history lesson is factually correct and furthermore I would not argue with you over the recap as I have not tested any of this out. I will take your word for it. I do find it interesting that there is a difference developmentally between Gnome Classic and Gnome Flashback. I also think that accurate expressions should be used as it avoids confusion. I remember reading something from Gnome.org about providing a classic session through Gnome extensions. I have found this

[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)

I am some what confused why Ubuntu Gnome does not give Gnome Flashback but installing Gnome Panel in Ubuntu does give Gnome flashback. Here is my explanation. The Ubuntu Gnome developers have not yet included gnome-panel 3.8.0 in Ubuntu Gnome. Whereas, installing the Gnome Panel package in Ubuntu, Edubuntu and Ubuntu Gnome Saucy does install gnome-panel 3.8.0. I am not basing this on evidence just supposition.

Regards.

---

