---
title: "gtk based F-spot replacement"
date: 2008-04-11
forum: Desktop Environments
---

### Post by eldragon on 2008-04-11
ok, i think personally that F-spot sucks.. plain and simple. thats how i feel, and i tried many times to learn to deal with the fact that its
a) unstable
b) poorly thought out
c) a clone of picasa.

im set out to find something better, that should sort pictures in folder hierarchy, not like fspot does, it should do it right. work with subfolders like it should (and not think its just another album...).

it should index pictures in a dbase so it doesnt have to every time i open an album like fspot does, but it should forget about those pictures once they are gone. (something i dont understand why fstop cant do).

it should tag those pictures too. it should multiple file tagging all at once. and it should give a simple way to view pictures like tags.
it doesnt need to be able to edit pictures (other than metadata). 

it should of course have a nice slideshow option. 

and last but not least. it should integrate with nautilus (so it doesnt have to generate  thumbnails every time i enter a pictures folder like it does).

and no. digikam isnt an option, i used to use digikam, im looking for an all-gtk program.

is there something like this in the gnome world?

---

### Post by nabl on 2008-04-11
I read an article on Linux.com a few days ago about a program for this called blueMarine, and I just found it:

[http://www.linux.com/feature/130449](http://www.linux.com/feature/130449)

You might want to check it out--it looks pretty nice. Sadly, it seems the website for the actual project is down. You might be able to find something with a little googling, though. ;)

Oh, and it's written in Java; I'm not sure which toolkit is used (is there a Java toolkit? I think so, but I can't remember at the moment).

EDIT: Like I said, the main site is down; however, the development site works, so you can use the SVN version if you're not worried about its instability.
(link: [https://bluemarine.dev.java.net/](https://bluemarine.dev.java.net/))

---

### Post by FakeOutdoorsman on 2008-04-11
F-spot also requires Mono and friends, which I don't particularly care for.  Might want to take a look at gThumb, but it might be too simplistic.

---

### Post by trippinnik on 2008-04-11
If you check F-spot's website they list a large list of alternatives. But really digikam is exactly want you want except for your disapproval of the toolkit.

---

### Post by eldragon on 2008-04-11
> **trippinnik said:**
> If you check F-spot's website they list a large list of alternatives. But really digikam is exactly want you want except for your disapproval of the toolkit.

ive been using digikam lately, but i want something that integrates with nautilus. and it feels so clunky to me.

ive read fspot has one of my most important needed feature on the todo list, so i better wait a bit. (folder browser pane)

too bad it still keeps segfaulting on me....otherwise i could put up with it for a while till they get their act together...

thaanks for the replies....


java is too damn slow... :(

---

### Post by trippinnik on 2008-04-13
What version of mono do you have installed (F-spot uses mono) and what version of Ubuntu do you have running?  Recent versions of mono have made some significant speed increases, although F-spot does load a bit slow (but probably still faster the Picasa).

---

### Post by eldragon on 2008-04-13
```

$ mono -V
Mono JIT compiler version 1.2.6 (tarball)
Copyright (C) 2002-2007 Novell, Inc and Contributors. www.mono-project.com
	TLS:           __thread
	GC:            Included Boehm (with typed GC)
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  x86
	Disabled:      none

```

is this what you ask for?
im actually running hardy beta.
ive searched for bug reports concerning f-spot crashing daily and found none.


edit:
im right now downloading the mono 1.9 installer from [www.mono-project.com](www.mono-project.com). is this a good idea? could this break my system?

---

### Post by LeoSolaris on 2008-04-13
> **eldragon said:**
> im right now downloading the mono 1.9 installer from [www.mono-project.com]("http://www.mono-project.com"). is this a good idea? could this break my system?

Any update has that potential, but it does sound like your best bet for the speed increase your looking for. Do a back up just to be on the safe side, since that is a central piece of Gnome, though if you're handy with it, you could always fix it through recovery mode. 

Leo

---

### Post by eldragon on 2008-04-13
> **LeoSolaris said:**
> Any update has that potential, but it does sound like your best bet for the speed increase your looking for. Do a back up just to be on the safe side, since that is a central piece of Gnome, though if you're handy with it, you could always fix it through recovery mode. 

Leo

hah, ive already installed, broke the thing entirely, and fixed it. so im back at square 1.


i guess i'll have to wait a bit till f-spot developers get right at my demands.....or i'll hold the world hostage with nuclear devices....muahahhahahah (dr evil-esque laughter):lolflag:

---

### Post by lee_connell on 2008-06-11
[QUOTE=Oh, and it's written in Java; I'm not sure which toolkit is used (is there a Java toolkit? I think so, but I can't remember at the moment).)[/QUOTE]

SWT is the toolkit

---

