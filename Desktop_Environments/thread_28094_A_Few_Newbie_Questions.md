---
title: "A Few Newbie Questions"
date: 2005-04-18
forum: Desktop Environments
---

### Post by laissezfaire on 2005-04-18
Hi everyone:
I am a newbie to linux and after trying several other distributions I have decided that Ubuntu is the most trouble free linux (for me at least). However, this doesn't mean that I am  not having any problems (mostly due to my being a newbie). Anyway here it goes:
1- I do not know how this happened but after installing several packages now when I launch a program, two instances of it are launced. The program is usually working but I can also see the other instance being launced by KDE. This goes on like for a minute and after that,  unable to start, the second instance (the jumping mouse icon) is gone. I wonder if this is a common problem and if there is a way to get rid of this annoyance.

2- AmaroK rocks but a have a few problems with this particular software namely:
a-    When I goto the configuration screen there are no engines listed that I can        select. This was the case when the amarok-arts package was installed by default and it is still the case when I uninstalled that and installed amarok-xine insted. The is no problem with the sound though.
b-    I wonder where Amarok saves user data so that I can backup my favorite songs information etc. if I need to reinstall everything in the future.
c-    Can I play mp3pro files without losing sound quality? Which engine should I use for it or do I need to install any additional codecs?

3- Is it posssible to place a "show desktop" icon on the bar next to the K-menu? This is a big convenience for me. Also how do I move the trashcan to the desktop again.

Any help is greatly appreciated.

---

### Post by ltmon on 2005-04-18
I had the same problem with amarok.  I decided to use gstreamer, and it's working fine.

Make sure you install

gstreamer0.8
gstreamer0.8-plugins
gstreamer0.8-mad

and

amarok-gstreamer

(Sorry if the package names aren't quite correct, I'm posting from work).

Amarok saves it's collection data in (I believe) 

~/.kde/share/apps/amarok/collection.db

Which is a sqllite database.

Cheers,

Luke.

---

### Post by denzilla on 2005-04-18
Are you double clicking to start a program, like windows? If your double-clicking, you could be starting the app twice.

---

### Post by lespedeza on 2005-04-19
In response to your first issue, the two instances of programs being started, I've experienced the same thing.  It doesn't happen with most applications, but the two with which it does occur are firefox and openoffice.  It's quite annoying and I've been trying to figure out what I've done, haven't done, and what I need to do to fix it.  I've experienced the exact behavior that you described, two instances show up in the taskbar, one opens fine and the other one just spins and spins, the icon continues to bounce and then it just goes away.  As far as the question about double-clicking, nope just single clicking and it still happens.  Any ideas, anyone?  Thanks.

regards,

jimmy

---

### Post by drumicube on 2005-06-11
Exactly the same for me, and no way to figure out where it may comes from...
I'm a newbie to KDE, so any suggestions are really welcome !
thanks !

---

### Post by Xian on 2005-06-11
[QUOTE=laissezfaire]3- Is it posssible to place a "show desktop" icon on the bar next to the K-menu? This is a big convenience for me. Also how do I move the trashcan to the desktop again.[/QUOTE]
There should be a special menu selection for this available when you right-click on the panel and choose to add items. This is a [method](http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#showtrash) which will allow you to place the trash bin on your desktop.

---

### Post by muzza on 2005-06-12
To add a 'show desktop' icon in the task bar.

Right click in the taskbar and select 'Add to Panel' -> 'Special Button' -> 'Desktop Access'

To place the new 'button' where you want it, right click on the new 'button' and select 'Move Desktop Access Button' then drag the button to its new home.

Note; you can only drag it within its taskbar. ( I have a taskbar on the top and the bottom.)

---

