---
title: "Gnome / GTK and tray / notification area apps"
date: 2008-12-23
forum: Desktop Environments
---

### Post by pelle.k on 2008-12-23
Hey people. This is *not* a support request. I just want to bring this up for discussion since it bothers me, and you may have some idea or insight into this that i didn't know about, so here it goes.

1. gnome-panel. It looks kind of ugly. It doesn't scale well because widgets mostly was designed for 22/24 pixel size. I would also like main meny buttons actually would look like real buttons, but one could argue they are only buttons like in a regular menu. The menu also scales badly when sizing the panel.
Same goes for icons (tray/applet/launchers). Some scale well while others are hardcoded, and others have no scalable icon, just 22/48 pixel sizes. Some try to scale, but end up looking like crap.
There's no option to add padding (or spacing) to elements in the gnome panel. It would be nice if there was a 1 or 2 pixel padding instead of icons reaching out to outer limit, while some do not. A padding would minimize the effect of that (visually). Same goes for the notification area. It looks really messy.
Found this the other day; [http://www.bomahy.nl/hylke/blog/ugly-notification-area-in-gnome/](http://www.bomahy.nl/hylke/blog/ugly-notification-area-in-gnome/)
Good read.

2. tray applications (or notification are applications).
I've tried a handful of music players these last days (all with a tray icon, because i like to get it out of my way i.e. window list). They all work differently. Some save their window position upon exit. Some save it when minimizing to tray. Some remember during the session, and then forget it. Some don't remeber it. Some remember it if you run compiz. Some open up centered on the screen, no matter what you do, and some open up in the left top corner, without any method of controlling that.

Maybe gnome and gtk developers should work on a common method for window placement, especially concerning tray applications, and the gnome devs do a little pimping on the gnome-panel.
I do realize this is often the fault of the individual application developers though, but if one were to provide gtk with a common method that takes care of tray/notification apps to a larger extent that it does, maybe we could take care of this problem once and for all, instead of picking on individual developers and applications.

Good rant. I needed that.

---

### Post by Copernicus1234 on 2009-01-01
I read that article a few weeks ago too and I think it would be great if the Gnome devs would clean up the looks of the Notification Area. Just having the option to set custom icons would improve things quite a lot, then you could set them all to be the same size.

---

### Post by loose111 on 2010-07-22
Often this is a substitute for minimizing the window, to avoid  cluttering the taskbar. For example VLC’s notification area has a menu  with a “Hide VLC media player in taskbar” item, and the [AllTray]("http://alltray.trausch.us/about.php")  utility exists for people who want “to have a program always running,  but easy to put out of the way”. That may make perfect sense to the  developers of those individual applications. But looking at the  operating system as a whole, it’s crazy. No competent designer, sitting  down to design an operating system from scratch, would say to themselves  “I know, let’s have two completely inconsistent ways to hide windows”.

===============
[Link Building Service](http://www.linkbuilderspro.com)
[Internet Web Marketing](http://www.grantcom.us/news/2007/alexa-ranking-importance.htm)

---

### Post by pelle.k on 2010-07-22
> **loose111 said:**
> But looking at the  operating system as a whole, it’s crazy. No competent designer, sitting  down to design an operating system from scratch, would say to themselves  “I know, let’s have two completely inconsistent ways to hide windows”.

Yes, i realize that. Applications should probably be either window centric, or applet centric. If an application is window centric, it should present itself on startup, and minimnize to the window list. If it's applet centric, it shouldn't appear (show a window) on startup, but only a menu (or window) on demand, and stay out of the window list.
I think the new indicator applets is the right way to go for that, and since i wrote that rant, several patches has been sent upstream (and accepted), and as we all know ubuntu has got it's own brand new "system tray", and IMHO things have improved quite a bit since then.

I still don't like apps that try to be both applications and applets at the same time though (rhythmbox and transmission comes to mind).

I think a dock with (application) context sensitive menus, and the ability to hide apps on autostart (such as when booting up) ala the OSX dock solves many of the problems of having a window list AND a notification area. Of course, that would probably probably introduce new problems, but (after having tried it for a while) it seems to be the better solution IMHO.
It doesn't have to be a "dock" really, but the ability to have context sensitive menus, in the launcher/window list would make a lot of sense for both transmission and rhythmbox, two examples of apps that are using the slightly more schizophrenic approach that you describe, where they can minimize to two places (one of where they can present the context sensetive menu, i.e. the tray area icon).

Maybe gnome3 will improve things a bit?

---

