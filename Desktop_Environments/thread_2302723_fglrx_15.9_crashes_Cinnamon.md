---
title: "fglrx 15.9 crashes Cinnamon"
date: 2015-11-12
forum: Desktop Environments
---

### Post by cobradabest on 2015-11-12
Okay, I'm using Ubuntu Studio with Cinnamon installed, and I'm wanting to start using the fgrlx driver for Ubuntu, because I plan to start playing some high-end games on it (Such as the upcoming Linux port of Batman Arkham Night), but from what I hear, the default open source driver isn't good for playing games.

So I downloaded the latest fgrlx driver from [here]("http://www.ubuntuupdates.org/package/core/wily/restricted/proposed/fglrx-installer-updates").

However, when I installed it and restarted Cinnamon, I get an error saying it crashed and has gone to "fallback mode" (which looks like kde, actually), and it asks if I want to restart cinnamon, but I do, the error pops up again. I remember this happening when I was using Linux mint as well. When I change the driver back to the default, Cinnamon is working fine again.

How can I use the fgrlx driver with cinnamon?

---

### Post by ajgreeny on 2015-11-12
Which version of US?

If you have installed 15.10 you will not get fglrx to work at the moment.  The hope is that there will be some movement on this known problem soon and that fglrx will be usable again.
[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Graphics_and_Display](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Graphics_and_Display)

---

### Post by cobradabest on 2015-11-13
> **ajgreeny said:**
> Which version of US?
Oh sorry, it's 15.10.

> **ajgreeny said:**
> If you have installed 15.10 you will not get fglrx to work at the moment.  The hope is that there will be some movement on this known problem soon and that fglrx will be usable again.
[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Graphics_and_Display](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Graphics_and_Display)
I hope so, thanks anyway!

---

### Post by cobradabest on 2015-11-13
Are there any alternative drivers other than the default and fglrx? I want to get a decent driver if I want to play games on thids...

---

### Post by Bashing-om on 2015-11-13
cobradabest; Hello;

Yeah, there are a couple of work-a-rounds while we await the fix to make it downstream ( testing upstream still in progress):
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)
[http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588](http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588) <- work-a-round
[http://ubuntuforums.org/showthread.php?t=2300920&highlight=FGLRX](http://ubuntuforums.org/showthread.php?t=2300920&highlight=FGLRX)
[http://ubuntuforums.org/showthread.php?t=2299981&highlight=FGLRX](http://ubuntuforums.org/showthread.php?t=2299981&highlight=FGLRX)

[INDENT][INDENT]good luck
[/INDENT][/INDENT]

---

### Post by cobradabest on 2015-11-13
**That worked! **Thank you so much! :D

---

### Post by cobradabest on 2015-11-13
Although I don't see the Catalyst control center program anywhere... do I have to install that separately?

Edit: I found out that you need to use the command line. The last time I successfully installed the driver, there were shortcuts automatically made for it... is there a way to get them back?

---

### Post by Bashing-om on 2015-11-14
cobradabest; Welp:
> 
Edit: I found out that you need to use the command line. The last time I successfully installed the driver, there were shortcuts automatically made for it... is there a way to get them back?

Let's see what is installed. 

```

dpkg -l | grep fglrx
lsmod | grep fglrx

```

Maybe consider reinstalling amdcccle (??) .

[INDENT][INDENT]maybe yes[/INDENT][/INDENT]

---

