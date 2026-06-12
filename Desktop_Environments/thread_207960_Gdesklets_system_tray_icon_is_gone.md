---
title: "Gdesklets system tray icon is gone"
date: 2006-07-02
forum: Desktop Environments
---

### Post by titancomputing on 2006-07-02
While I was super customizing my desktop, I downloaded gdesklets for the nice widgets. Well in an attempt to be slick, I turned up translucency and told it to not show the system tray icon. Well, now I need that icon and can't find out how to get it back. Does anyone know the way to make the icon reappear so I can fix my translucent nightmare?

---

### Post by Thund3rstruck on 2006-07-02
yea
```

CTRL+ALT+Backspace

```

Don't waste your time with gDesklets. It crashes every 10 minutes or so. I have never had it run an entire login cycle and thats with multiple kernels on multiple systems

---

### Post by orb9220 on 2006-07-03
I am sorry but I have been running gDesklets about 7 of them with no problems.

I like the way people condem an app just cuz they have problems with them.

Well to yer problem. 

Did u change the transparency off on bar to see if it reappers with the other tasks in sys tray?

If you righ-click congig > configutation is Translucency checked or unchecked.
Mine is unchecked.
 Is Behavior checked for Show tray icon?

That's all for now. And in the future take what any individual says with a grain of sand when they make wide sweeping statements.

At least a great majority of problems with any app on systems are specific to software or hardware issue's like type of video card or to specific to motherboard ect.

Unless you see the same problem over and over on different machines and distro's Then and only then do I start looking for a bug to that specific machine.

Hope this help's you and you may want to try different theme's to see if it is a 
still a problem.

---

### Post by titancomputing on 2006-07-03
Nah, the thing is, I told it to not even display the system tray icon so I can't mess with the translucency. Is there a way to make the icon reappear again so I can change it?

---

### Post by noth1ng on 2006-11-01
Hi, sorry for digging up such an old topic, but i have recently had the same problem and i really need someone to help me with it. I can't change the translucency-thingy, 'cause there's no Gdesklet notification area icon 'cause i also didn't want in to be shown](*,) . Now i need it really bad. Maby someone can help me.

---

### Post by almahtar on 2006-11-01
You may have to re-configure some desklets if you do this, but open your home dir in nautilus, hit control + h to show hidden files.

Go into the ".gdesklets" folder, go into the "registry" folder, and you'll see a file called "config<some crazy number>.db"

Delete it, log out, and log back in.

Tell me if that helps.

---

### Post by noth1ng on 2006-11-01
Thanks, man, that worked like a charm. And as I didn't have any desklets installed, it didn't screw anything up either. One problem less to worry about now (believe me, there are a lot of them left:mrgreen: ).

---

### Post by almahtar on 2006-11-06
Sure thing, and good luck with your other problems!

I didn't even think of it, but in the future you could solve the same problem by firing up synaptic and selecting to "completely remove" gdesklets (not just "remove).  When you "completely remove" a package it gets rid of all the package's config files as well.  After that, just re-install the package.

---

