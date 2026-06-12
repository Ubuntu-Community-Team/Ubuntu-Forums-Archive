---
title: "Any dock withouf Compiz???"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by Dojan5 on 2008-01-04
I have searched the forums, i found one called Cairo dock... I cant run it, or rather, i dunno how to install it. I am currently using SimDock, 1.2 BETA...
It is good looking, once you disable the magnification, and well, theres one thing quite, irritating.
The dock is terribly dispositioned! 
And sometimes it looks like the second...
So, now im scouting for a new dock, sure, i have heard of AWN, i did have it installed.
But, i cant run Compiz... So, is there any other transparent dock that dont require compiz 
or, is there any way of running kiba or awn without compiz???
Thanks
/
Joel

---

### Post by P4oL1n0 on 2008-01-04
Have you tried the new Cairo Dock? you can find an HowTo here [http://doc.ubuntu-fr.org/cairo-dock]("http://doc.ubuntu-fr.org/cairo-dock")

Although it isn't in English (the howto), installation is very intuitable...

---

### Post by Dojan5 on 2008-01-04
Umm, yaa, i took a look on it...
 Cairo-dock is a launch bar hosted applications (or dock), which appears on the desktop.
To run, you must set up an interface 3d or composite
[http://translate.google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fcairo-dock&langpair=fr%7Cen&hl=en&ie=UTF8]("http://translate.google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fcairo-dock&langpair=fr%7Cen&hl=en&ie=UTF8").
So, is there any other composite manager than compiz??

Oh wait, that was the exact dock that i downloaded. But i cant get it running...

AGH!
I cant edit my sources.list :S

---

### Post by P4oL1n0 on 2008-01-04
You're right... sorry but I was sure that it run without any composite manager..... :(
Unfortunately most of dockbar needed a CM.... you can try the dock of gDesklets, a little old but very easy to configure.

Sorry but I don't know any others.

---

### Post by P4oL1n0 on 2008-01-04
> **Dojan5 said:**
> Umm, yaa, i took a look on it...
I cant edit my sources.list :S

What is the problem?

---

### Post by andrewsomething on 2008-01-04
Have you tried using xcompmgr? It's a much simpler compositor than Compiz. You don't get all the fancy effects, but you do get true transparency. It will also allow you to run AWN or most any other dock that needs a compositor. It's more light weight than Compiz, and might work with your graphics card. It's in the repos so just install with:
```
sudo apt-get install xcompmgr
```

---

### Post by Dojan5 on 2008-01-05
> **andrewsomething said:**
> Have you tried using xcompmgr? It's a much simpler compositor than Compiz. You don't get all the fancy effects, but you do get true transparency. It will also allow you to run AWN or most any other dock that needs a compositor. It's more light weight than Compiz, and might work with your graphics card. It's in the repos so just install with:
```
sudo apt-get install xcompmgr
```

I solved it my self, thanks anyway...
What i did was open the directory wich the file is in and double click on it.
I found that simpler than finding the program, anyway, i just added a line and it worked...
Thanks...
Umm, well i did solve the dock problem too.
Really simple actually, i just made a new panel.
Made it transparent, added a few things, like a drawer the home directory gimp firefox terminal and so on and unchecked the thing "fold out" or something in the panel properities. Though, the only problem is that if i have something maximized, itll have a lot of space since the dock is on top...
Wonder if i can make it non top?
Anyway, thanks yall!

---

### Post by Faud on 2008-01-05
You can add a panel to the top, bottom, left or right of the desktop.

---

### Post by Dojan5 on 2008-01-07
> **Faud said:**
> You can add a panel to the top, bottom, left or right of the desktop.

Well, when i maximize something like FireFox i still see a part of my desktop...
Like, firefox wont be above the panel...

---

