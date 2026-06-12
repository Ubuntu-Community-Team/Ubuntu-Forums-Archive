---
title: "Screen random;ly flashes/refreshes when hitting &quot;tab&quot;"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Seamus on 2006-07-20
Hi,

This week I upgraded from FC4 to Dapper - great move, and loving it.

The only major bug I have here is that I get the screen "flashing" when I hit the tab button to "auto-complete" the command line strings I am entering. AS you can imagine this is really annoying and a bit hard on the eyes :(

IT also does it randomly at other times as well.

This never ever happened when running under FC4, so I am a little unsure what could be causing it. The only hardware difference under Dapper from FC4 is that I have my old harddrive from FC4 mounted until I complete the transfer across of data.

I ran lspci and got this:

VGA compatible controller: Intel Corporation 82865G Integrated Grap hics Controller (rev 02)

I have an HP d530S P2.4 machine.

ANy help solving this REALLY annoying bug would be greatly appreciated.

Cheers,

---

### Post by Seamus on 2006-07-20
OK! wow, may have a fix for this one already. under terminal settings

"Edit" -> "Current Profile" there is a setting there "terminal bell" that is ticked by default. Turn this off, problem goes away.

Geez, I am glad I have a techo here at work old enough to know what "Bell" is all about ;)

hope this helps someone else ;)

---

### Post by Seamus on 2006-07-27
OK I am reopening up this one. looks like there are other key combinations that are triggering the terminal bell / system bell alert. Any ideas how to turn this off in gnome system wide?

Cheers!

---

### Post by Seamus on 2006-07-27
> **Seamus said:**
> OK I am reopening up this one. looks like there are other key combinations that are triggering the terminal bell / system bell alert. Any ideas how to turn this off in gnome system wide?

Cheers!

OK found a fix in this thread 

[http://ubuntuforums.org/showthread.php?t=192463&highlight=terminal+bell](http://ubuntuforums.org/showthread.php?t=192463&highlight=terminal+bell)

> 
System --> Preferences --> Sounds
setup your own sounds, then go to system beep tab and uncheck it.

why the heck it was on by default I will never know, but I am SO glad it is turned off.

---

