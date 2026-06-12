---
title: "How to: Install ScummVM compatible games"
date: 2014-03-31
forum: Gaming &amp; Leisure
---

### Post by arodulfo on 2014-03-31
Dear all,

There are not so many helpful hints on using ScummVM in (X)Ubuntu.
I happen to be using XUbuntu and, at the same time, a LucasFilm Games lover.

User **ibbuntu** did a wonderful job helping us all to properly get CD version of Loom up and running in our systems.
Just check the [link]("http://ubuntuforums.org/showthread.php?t=536748") to his/her post.:D

Did I mention I am a bit lazy (well, in fact, more than a bit)?
I have no problem using ScummVM interface ti run my games but, what if I can use them directly from Applications menu (remember I am using XFCE)?
That's how *Beneath a Steel Sky* or *Lure of the Temptress* end up installed if you use Ubuntu Software Center to get them.

After some exploring on my system and a couple of tests, I managed to have kind of a procedure to have any ScummVM compatible game installed and running with a shortcut in Applications menu:
[LIST]
[*]Download or create an icon, in PNG format, and name it after the game (just to have an easy remembering). In our case, let's name it *loom.png* (it has been included in my attachment) 
[*]With *root* rights, place the icon into */usr/share/pixmaps*, so that the system can locate and show it 
[*]Place the game files (with root rights) on the proper folder. They seem to prefer placing the games under */usr/share/scummvm/game*, being "game" the name of yours. 
[*]Create a desktop direct access file. I have attached a demo desktop file, loom.desktop, tailored to Loom needs. Make sure the game files are in the folder the desktop file points to. Copy the desktop file (with root rights) to */usr/share/applications*. 
[*]Optionally, create a script to invoke the game out of CLI. It can be useful. I have included a sample (named *loom*) in my attachment. With root rights, copy the script to */usr/games*. 
[/LIST]

Eventually this all will end with a new entry in your Applications menu, Games section, with the proper icon, allowing you to directly execute Loom from there.
You can play with the options used when invoking ScummVM, so you can adapt the direct access file to your own needs.

I hope this modest howto will help other newbies, like me, to play their favourite old-fashioned games with their favourite operating system. :D

Kind regards,

---

