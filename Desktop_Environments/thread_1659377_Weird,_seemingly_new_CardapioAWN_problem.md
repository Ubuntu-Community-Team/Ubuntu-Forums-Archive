---
title: "Weird, seemingly new Cardapio/AWN problem"
date: 2011-01-03
forum: Desktop Environments
---

### Post by Kalimol on 2011-01-03
I find this strange: Cardapio is rendering within a GTK border and with the application background instead of the menu one. It doesn't do this with the Gnome panel applet, but it does when launched from the AWN applet, or if I run it from command line. 

[IMG]http://i146.photobucket.com/albums/r256/Kalimol/Screenshot-4-1.png[/IMG]

What's rather vexing about this is that if I have my AWN dock at the bottom of the screen and try to launch the menu, it draws the window with its upper-left corner starting at the applet, meaning that it's positioned almost entirely below the screen edge. Of course, even though it's in a frame, Cardapio still can't be moved, either, making it unusable, hidden behind the dock. (I wouldn't know it was there if not for the dock's transparency.)

Any ideas? Is this a new bug, or is there something I don't know? Thanks for any help....

---

### Post by tvst on 2011-01-09
Hello, I'm one of the Cardapio developers. 

The window frame was added (on purpose!) after a few users (and another Cardapio developer) said they preferred it that way. If you like it without the frame, please open a bug report or feature request here:

[https://bugs.launchpad.net/cardapio/](https://bugs.launchpad.net/cardapio/)

Similarly, you should also report the other issue you are experiencing, where Cardapio is being positioned below the screen edge. Just make sure you open a separate report for that one :)

I know opening bug reports may seem somewhat redundant, given that I have already seen this forum post, but a proper bug report actually makes the developers' lives easier and so it becomes more likely that we'll fix the problem...

Cheers

---

