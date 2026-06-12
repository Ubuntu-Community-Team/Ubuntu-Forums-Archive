---
title: "x.org and cpu usage"
date: 2005-08-25
forum: Desktop Environments
---

### Post by tonysathre on 2005-08-25
i downloaded a system monitor theme and run it with super karamba.  i noticed that my cpu usage was always at least 20 - 24 percent, even if i didnt have anything open.  so i opened a terminal and typed top and x.org was on top using a colossal 19 - 22% at all times.  what can i do to make x.org use much less cpu power

thanks in advance

---

### Post by incinerator on 2005-08-25
1. shut down superkaramba and check what the cpu usage is without it
2. tell more about your system: what cpu, how much ram, how big are the hard disks, what gfx card.

---

### Post by tonysathre on 2005-08-25
i have a dell 4550 with a 2.53 ghz, 512 mb ddr ram, geforce4 mx 420 gfx card, hda is 60 gb, hdb is 8.6 gb, i shut down superkaramba and it was only using no more than 1%, superkaramba isnt the problem

---

### Post by incinerator on 2005-08-25
Are you trying to say that
- WITH superkaramba running xorg eats 20% cpu time
- WITHOUT superkaramba running xorg eats only 1% cpu time?

---

### Post by Takis on 2005-08-25
[QUOTE=incinerator]Are you trying to say that
- WITH superkaramba running xorg eats 20% cpu time
- WITHOUT superkaramba running xorg eats only 1% cpu time?[/QUOTE]
And that somehow SuperKaramba *isn't* the problem...?

---

### Post by DrQuincy on 2005-08-26
I've having the same problem.  Xorg-debug also drains my CPU when Super Karamba is running.

---

### Post by Takis on 2005-08-26
You need to keep in mind that SuperKaramba is a program that is constantly updating itself. It needs to do quite a bit of work to keep your desktop eyecandy up to date, so what you're seeing here isn't a bug - it's like asking about CPU usage when you've a media player open.

As long as you're not running anything that requires massive amounts of CPU, having Xorg take up 25% of the CPU is fine. If you're going to open a game or something, you may like to shut SuperKaramba down though.

---

### Post by Freddy on 2005-08-27
> i have a dell 4550 with a 2.53 ghz, 512 mb ddr ram, geforce4 mx 420 gfx card, hda is 60 gb, hdb is 8.6 gb, i shut down superkaramba and it was only using no more than 1%, superkaramba isnt the problem 
I think he meant that Superkaramba only used 1% and that Superkaramba wasn't the problem  /// Freddan

---

### Post by incinerator on 2005-08-27
[QUOTE=Freddy]I think he meant that Superkaramba only used 1% and that Superkaramba wasn't the problem  /// Freddan[/QUOTE]

Fair enough, but it hardly is superkaramba that is undertaking the task of updating the display n times a second, is it?
Displaying stuff costs cpu time, too. Particularly superkaramba with its abundance of eyecandy (e.g. translucency) requires the X server to do quite a lot of work.

Some cpu time saving may be gained by tuning the x-server setup, particulary enabling 2d accelleration in this case. Enabling the RENDER extension in xorg.conf may help. In case of nvidia gfx cards you could also change the driver from "nv" to "nvidia", that my yield some improvements in 2d acceleration and therefore savings in cpu time. Information about that is in the wiki ([here](https://wiki.ubuntu.com/NvidiaManual) and [here](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)) and in the [unofficial user guide](http://ubuntuguide.org/#installnvidiadriver). I am sure similiar docs can be found for gfx cards with ATI chips on it.

---

### Post by tonysathre on 2005-08-29
thanks for the help..ill check out those links, and ya i meant superkaramba uses only 1%

---

### Post by Takis on 2005-08-29
I worded it badly. Incinerator got it right on the money, though - SuperKaramba uses a number of graphical features available in Xorg. Due to the nice modularisation in Linux, this means the designer of SuperKaramba could say (in a very abstract way, here) 'Xorg.makeTranslucent(myWindow)' and wouldn't have to program all that crap.

All that's happening is SuperKaramba passes the work onto Xorg. It's perfectly natural to have a jump in CPU usage for often-refreshed sweet graphics - otherwise, we wouldn't have such high-end requirements for games.

---

