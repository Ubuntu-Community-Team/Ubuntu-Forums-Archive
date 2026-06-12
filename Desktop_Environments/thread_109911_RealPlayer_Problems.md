---
title: "RealPlayer Problems"
date: 2005-12-29
forum: Desktop Environments
---

### Post by diffuser78 on 2005-12-29
This has become a classical problem for me to solve on Ubuntu.

I listen to musin on websites such as [www.raaga.com/hindi](www.raaga.com/hindi)

This needs firefox plugin for Realplayer and till date I have not been able to play music on this website or for that matter sites which needs Firefox plugin for Realplayer.

I have installed all helix codecs and did everything but couldnt do it.

I am wondering if there is anybody around who has played around enough to get this things working.

There are also some posts under my name which are atleast 4 months old when I had tried enough to get the realplayer working on firefox to play the music on [www.raaga.com/hindi](www.raaga.com/hindi)

Any and every help is appreciated.

Please make my Ubuntu experience even more enjoyable.

Thanks for your time,

---

### Post by Perfect Storm on 2005-12-29
If you are using i386 structure:

First uninstall the helix player.

Then

```
 sudo gedit /etc/apt/sources.list 
```

Add:

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

```

sudo apt-get update
sudo apt-get install realplay

```

That should do the trick.

---

### Post by diffuser78 on 2005-12-29
I tried the trick you told me but it was not enough to play the music on the [www.raaga.com/hindi](www.raaga.com/hindi)

Could you play any music file on the above mentioned webpage.

Thanks for your help,



[QUOTE=Artificial Intelligence]If you are using i386 structure:

First uninstall the helix player.

Then

```
 sudo gedit /etc/apt/sources.list 
```

Add:

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

```

sudo apt-get update
sudo apt-get install realplay

```

That should do the trick.[/QUOTE]

---

### Post by DaMasta on 2005-12-29
I think that qualifies as embedded realplayer. I've had difficulty with that as well when trying to view [http://philadelphiaeagles.com](http://philadelphiaeagles.com). I'd like to know about this as well.

---

### Post by diffuser78 on 2005-12-29
Thats true, it should be called embedded real player as my real player works like a charm. Only when I need to play the music on the website [www.raaga.com/hindi](www.raaga.com/hindi) does it stalls.

Any pros around can put some feedback.



[QUOTE=DaMasta]I think that qualifies as embedded realplayer. I've had difficulty with that as well when trying to view [http://philadelphiaeagles.com](http://philadelphiaeagles.com). I'd like to know about this as well.[/QUOTE]

---

### Post by art on 2005-12-30
Have you tried getting mozplugger to embed realplayer?

---

### Post by diffuser78 on 2005-12-30
I installed mozplugger but it didnt helped me. It also uninstalled mozilla-acroread in the process.

Can you play the music in ur Ubuntu using firefox ?

[QUOTE=art]Have you tried getting mozplugger to embed realplayer?[/QUOTE]

---

### Post by art on 2005-12-30
Which version of Firefox are you using?

---

### Post by dcstar on 2005-12-30
[QUOTE=diffuser78]I installed mozplugger but it didnt helped me. It also uninstalled mozilla-acroread in the process.

Can you play the music in ur Ubuntu using firefox ?[/QUOTE]
I have FF 1.07 that plays other streaming Real Audio content ok, but it won't play stuff from that site - so it's not just your setup!

I'd e-mail the site and ask them to look into the problem.

---

### Post by art on 2005-12-30
Yeah, the same here, I have FF 1.5, and it plays stuff from [http://www.yolinux.com/TUTORIALS/LinuxTutorialMozillaConfiguration.html#PLUGINS](http://www.yolinux.com/TUTORIALS/LinuxTutorialMozillaConfiguration.html#PLUGINS) 
 in RealPlayer, but not the philadelphiaeagles nor the indian one...

---

### Post by encompass on 2005-12-30
Realplayer can do this kind of support.  I have realpaly it is works just fine for everything I do.  There new play is rather simple to install and this time uses the gtk interface.
I say talk to Real and see if they can fix it for you.  The make their software and don't let others touch the codec so you can ask them for the answer.

---

### Post by art on 2005-12-30
[QUOTE=encompass]Realplayer can do this kind of support.  I have realpaly it is works just fine for everything I do.  There new play is rather simple to install and this time uses the gtk interface.
I say talk to Real and see if they can fix it for you.  The make their software and don't let others touch the codec so you can ask them for the answer.[/QUOTE]
 Do you mean you can play 

[www.raaga.com/hindi](www.raaga.com/hindi)

and [http://philadelphiaeagles.com](http://philadelphiaeagles.com) sites?

---

### Post by diffuser78 on 2005-12-31
Thanks guys for your support!!!

Keep us posted if you can get something.

---

