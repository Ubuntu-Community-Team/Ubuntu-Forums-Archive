---
title: "Lubuntu , Openbox , Change default icon in window title bar."
date: 2014-10-28
forum: Desktop Environments
---

### Post by AndrewPine on 2014-10-28
I've been a huge fan of LXDE , Lubuntu and Openbox for several years.

But there has been one thing that has bugged me. 

When you open a window that does not have it's own dedicated icon (firefox, abiword etc) it shows this icon (shown below) , it's roughly the same icon that shows up when a Microsoft Windows application/window locks up and "stops responding" and is generally not to my taste. 


How can I change this? I don't mind if it simply means over-writing certain .png files etc.


[IMG]http://s30.postimg.org/eu8hqppf5/Open_Box_Icon.png[/IMG]


Link to same image: [http://s30.postimg.org/eu8hqppf5/Open_Box_Icon.png](http://s30.postimg.org/eu8hqppf5/Open_Box_Icon.png)

Cheers , Andrew

---

### Post by vasa1 on 2014-10-28
In case you don't get a satisfactory answer here, try the Openbox mailing list @ [http://icculus.org/mailman/listinfo/openbox](http://icculus.org/mailman/listinfo/openbox). That's where Openbox devs visit.

BTW, I see the same thing you do :(

---

### Post by AndrewPine on 2014-10-28
Cheers for that, is there any way to communicate **to** them?


If I could track down that specific icon file(s) in question (in it's actual folder) and replace them with the one(s) I want that should do the trick.


I found identical icons in /usr/share/pixmaps/ named openbox.png and openbox.xpm but that did not work.

---

### Post by vasa1 on 2014-10-28
I think they'd prefer being approached via the mailing list so that more people benefit. So that would be my first choice.

I mostly see that "generic" icon when internal windows appear. One example I can readily recall is if I'm using Geany and want to do a search & replace, that secondary window doesn't have its own icon or even Geany's but the generic one.

But there are "primary" windows that show this generic icon as well. gPaint is one. I haven't really figured out how or why its supplied icon doesn't appear. Sorry I can't be of any help here!

---

### Post by vasa1 on 2014-11-17
Someone asked [a very related question]("https://plus.google.com/u/0/communities/114160725016062382822/stream/0c4f3725-9fa3-4078-81a8-3b40f17c0b77") on Google+ and that led me to these two links:
[http://crunchbang.org/forums/viewtopic.php?id=33673](http://crunchbang.org/forums/viewtopic.php?id=33673) ::: using correct icons instead of the default openbox one
[http://unix.stackexchange.com/questions/16774/how-to-assign-an-icon-to-a-program-in-openbox](http://unix.stackexchange.com/questions/16774/how-to-assign-an-icon-to-a-program-in-openbox)

Unfortunately, *xseticon* isn't in the software center though there's a .deb for it elsewhere. It's an itch waiting to be scratched ;)

Edit: further down that Crunchbang thread, the OP indicated that using fbpanel (in place of tint2) makes installing xseticon unnecessary. So that's what I'll try first.

---

