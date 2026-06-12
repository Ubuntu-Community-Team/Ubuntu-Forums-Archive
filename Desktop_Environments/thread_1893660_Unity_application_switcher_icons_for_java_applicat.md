---
title: "Unity application switcher icons for java applications"
date: 2011-12-10
forum: Desktop Environments
---

### Post by aaberg on 2011-12-10
Hi,

I have a problem with the unity applications switcher (ALT + TAB) in Ubuntu 11.10.

Two of the applications I use the most, are IntelliJ IDEA and muCommander. These are both java applications, that is started by executing a shell script. 

Both of these applications doesn't get the right icon in the unity application switcher, instead there is an annoying question mark icon.

These two applications are not the only examples, I think it happens to all java applications? It is sometimes hard to figure out what application I am switching to, when I have 3 or 4 of these question marks in the application switcher.

Anybody knows how to fix this?

---

### Post by aaberg on 2011-12-11
Hmm, I just installed the gnome-shell, just to try it out. In the gnome-shell this problem is non existing. Also, Gnome 3 seems to be more responsive and more stable. So I guess I will be using gnome instead of Unity for now.

If anyone have a solution for the problem, though, I am still interested in hearing it :)

---

### Post by Morgen on 2011-12-12
This appears to be related to a known issue in gnome shell where java applications use the system tray icon, which looks very poor in the switcher, favorites, etc. See the following Redhat bug:

[https://bugzilla.redhat.com/show_bug.cgi?id=683768](https://bugzilla.redhat.com/show_bug.cgi?id=683768)

They have a fix but I don't know if it was backported yet.

You could also take a look at this blog post regarding IntelliJ IDEA specifically:

[http://locademiaz.wordpress.com/2011/08/30/turn-your-java-apps-gnome-shell-friendly/](http://locademiaz.wordpress.com/2011/08/30/turn-your-java-apps-gnome-shell-friendly/)

---

