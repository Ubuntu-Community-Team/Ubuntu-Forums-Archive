---
title: "[SOLVED] Editing Nautilus settings, returning defaults"
date: 2010-06-07
forum: Desktop Environments
---

### Post by afrodeity on 2010-06-07
I finally have a working nautilus after weeks experiencing a seg fault caused by a dependency problem which I have only now managed to resolve.

It came right after doing this:

```

gconftool-2 --recursive-unset /apps/nautilus

```

I then removed nautilus-elementary ppa and downgraded the nautilus-data.

Problem is the nautilus I get is extremely minimal -- really just a window -- which insists on opening new windows whenever I click on a folder.

[http://www.flickr.com/photos/14887361@N05/4624055717/](http://www.flickr.com/photos/14887361@N05/4624055717/)

I've tried removing .nautilus on several occasions.

What are the default settings?

Is there a more convenient way of editing nautilus?

Striks me this has something to do with settings gconf. I'm going to play around and see if any of them fix this creature.

---

### Post by afrodeity on 2010-06-07
Solved it: 

Alt-F2

type: gconf-editor

Go to Apps > Nautilus > Preferences > Always use browser enable

My browser was disabled as the lucid upgrade failed to deal with the possiblity I had nautilus-elementary installed.

We really need to figure out a better way forward, since Nautilus-Elementary is really awesome when it works.

---

### Post by cheyo on 2010-10-21
Hey, this works!

I upgraded from lucid 32 bit to Maverick 64 bit and nautilus elementary had this "blank search" bug, so i returned to the "bundled" nautilus, but the edit/preferences dialog was gone. 

Following your advice, i did this 

* del ~/.nautilus

* Alt-F2

* type: gconf-editor

* Go to Apps > Nautilus > Preferences > CHECK AND UNCHECK "Always use browser enable"

* killall nautilus

Problem solved! preferences dialog is back.

Thank you afrodeity! :)

---

