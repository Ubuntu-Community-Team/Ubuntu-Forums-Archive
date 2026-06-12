---
title: "Toolbar shows on the desktop, not on the window"
date: 2007-12-26
forum: Desktop Effects &amp; Customization
---

### Post by javipas on 2007-12-26
Hi all,

I'm getting some weird behaviour on my Ubuntu apps. When they show up, the toolbar is not integrated in the window... it appears on the upper left corner of the desktop just below the Ubuntu toolbar panel. I've included a screenshot so you can see by yourselves...

[IMG]http://www.javipas.com/wp-content/gutsy1.jpg[/IMG]

I'd like to know how can I re-integrate these toolbars into their applications, I really don't know that to do with this annoying problem...

Any ideas? Thanx!

---

### Post by Ub1476 on 2007-12-26
I think you have downloaded the [Mac menu-bar hack for Gnome]("http://ubuntuforums.org/showthread.php?t=241868"). You can either choose to add the mac applet the panel or reinstall the hacked GTK. There should be some info somewhere in that thread.

---

### Post by javipas on 2007-12-26
> **Ub1476 said:**
> I think you have downloaded the [Mac menu-bar hack for Gnome]("http://ubuntuforums.org/showthread.php?t=241868"). You can either choose to add the mac applet the panel or reinstall the hacked GTK. There should be some info somewhere in that thread.

I tried to reinstall libgtk-2.0, and also removed the macmenu packaged, but no luck. The toolbar still appears on the corner, not on the applicaction. Too bad. It's weird, because on Firefox, for example, the toolbar is on the right place, but other apps - gnome terminal, GIMP, totem, etc - the behaviour is wrong.

Too bad. :( Thanks anyway... and merry chistmas, btw!

---

### Post by Forlong on 2007-12-26
> **javipas said:**
>  It's weird, because on Firefox, for example, the toolbar is on the right place, but other apps - gnome terminal, GIMP, totem, etc - the behaviour is wrong.
That's because:
> this gtk mac menu hack won't work with XUL apps (ie : firefox) Java swing apps (ie : open office) and all kde apps or non gtk apps
[https://wiki.ubuntu.com/global_menu](https://wiki.ubuntu.com/global_menu)


So how did you install the hack in first place?
Right now you are pretty much the only person that can know what has to be undone.
But this should be a good start: [https://wiki.ubuntu.com/global_menu#uninstall](https://wiki.ubuntu.com/global_menu#uninstall)

---

