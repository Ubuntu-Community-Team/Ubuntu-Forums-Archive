---
title: "cube"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by prapanj on 2007-10-28
i installed ubuntu just now..
but as i see in the videos.. i dont get a cube.. i actually have only 2 desktops. not 4.. for a cube.. so when i enabled cube and rotation.. i can only rotate a plane.. plz help

---

### Post by matthew.lns1 on 2007-10-28
Install compizconfig-settings-manager. It will give you that option. Though it can be hard to use at first.

---

### Post by Tanker Bob on 2007-10-28
In the basic desktop setup (Configure Desktop?), set the # of desktops to 1. Then in the Compiz settings, General options, set the horizontal virtual size to 4, vertical to 1, and # desktops to 1. Then execute:

```
dcop kicker default restart
```

You should then have 4 virtual desktops and the cube will no longer be a plane. Don't ask me why this works as it makes no sense to me, I just know that it does. The exact menus and directories will probably be different if you're using Gnome, because I'm using KDE.

In my /home/.kde/Autostart/ folder, I created two scripts. One starts compiz, the other refreshes the kicker and must run second. They don't always run in the correct order and sometimes don't run at all, so I put them on my desktop for quick, convenient access after reboots.

---

### Post by AvengingAngel718 on 2007-10-28
i'm pretty experienced with ubuntu but i'm having problems with my cube too. i tried to reinstal beryl from the feisty repos so i could have snow again, which worked, but it messed up compiz and some of the beryl stuff didnt work, and i had to uninstall compiz and beryl and it was all a huge mess...anyway, to make a long story short, i got compiz back and set it all up, but i only have a plane now, not the cube. i remember it took some messing around to get it working in the first place, but i know i did it and it's frustrating me. i already went into general options on my settings manager and set it to 4 desktops but it wont give me the cube.

also, i dont know if this is related, but when i go to my appearance preferences > visual effects and select custom set of effects, close it, and go back to it, it shows that i'm using "extra" effects, not the custom set, although it still does things the way i set it up to do. i'm pretty sure it didnt do this before :/

---

### Post by AvengingAngel718 on 2007-10-28
lol ok tanker bob posted just while i was typing....i tried that and it worked, so thanks a lot.

another day is saved by the ubuntu forums XD

---

