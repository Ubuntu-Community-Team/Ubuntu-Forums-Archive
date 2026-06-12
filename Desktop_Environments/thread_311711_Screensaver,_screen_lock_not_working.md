---
title: "Screensaver, screen lock not working"
date: 2006-12-03
forum: Desktop Environments
---

### Post by pertti on 2006-12-03
Hi,

I've been having some problems with Gnome Screensaver since I upgrade from Dapper to Edgy a couple of weeks ago. Screensaver preview works fine (all of them), but when it's time for it to show up nothing happens. Also, the screen lock doesn't work. The screen should lock itself when the screensaver appear, but it doesn't. Furthermore, neither closing the laptop lid nor manually locking the screen work.

I've seen [some threads]("http://www.ubuntuforums.org/showthread.php?t=288651") about problems with the screensaver, but not quite like mine (but I guess they are related). Is there any know workaround? Or at least somewhere (logs, etc) where I could gather some more information before submitting a bug to Launchpad?

Thanks in advance

---

### Post by syrleb on 2006-12-03
when you lock your computer, with the lock screen button, what happens?  because i no longer have a screen saver anymore either, just a blank white screen, but it locks, and it doesnt bother me anyway

---

### Post by pertti on 2006-12-03
Hi. The lock screen button doesn't work either. There's no way I can get the screen lock to work (screensaver, screen lock button, closing the lid of the laptop). The closest thing to a screensaver I can get is when I close the laptop lid the screen goes black. It's not the screensaver I've choosen, they screen isn't locked, but, hey, at least it doesn't consume that much power :).

---

### Post by talz13 on 2006-12-04
I'm having the same problem right now as well. I have my server running on a kvm switch on my parents desk, and since my remote stuff is having issues, I have to run the desktop from the local machine.  I don't want to leave this unlocked, as I don't know what they would do if they started messing around with it, but I thought, I'll just lock it and swap back to the other machine.

Nope!

ctrl+alt+L, quit->lock screen, lock screen menu item, nothing works.  It just sits there at the desktop not doing a thing.

Any clue why I can't lock the screen?  I'm just running an updated 6.06 here.

---

### Post by LookTJ on 2006-12-05
> **pertti said:**
> Hi. The lock screen button doesn't work either. There's no way I can get the screen lock to work (screensaver, screen lock button, closing the lid of the laptop). The closest thing to a screensaver I can get is when I close the laptop lid the screen goes black. It's not the screensaver I've choosen, they screen isn't locked, but, hey, at least it doesn't consume that much power :).

I have same problem.

problem:

lockscreen button works

when screensaver shows up, it's completely blank or black

Solution i have found:

None so far.

---

### Post by Phenz on 2006-12-19
I'm having the same problem after upgrading to edgy:

*No lock screen (Nothing happens when buttons or key commands pressed)
*No screensaver

I can also test and preview all screensavers ...


I'm using ATI Divers 8.28.8 on a Mobility Radeon X1400.  Any clues on how to fix this?

---

### Post by pertti on 2006-12-19
> **Phenz said:**
> I'm having the same problem after upgrading to edgy:

*No lock screen (Nothing happens when buttons or key commands pressed)
*No screensaver

I can also test and preview all screensavers ...


I'm using ATI Divers 8.28.8 on a Mobility Radeon X1400.  Any clues on how to fix this?

I haven't found any solution yet, but I'm guessing the ATI drivers are to blame: I have the same card!.

I also have another video-related problem: I can't watch video properly using Xv. In Dapper, the colors of the video were wrong when using Xv. I switched to noXv (I'm not sure right now), and from then colors were fine, but there were some problems with video size (full screen video doesn't like nice at all...). So, I've been using MPlayer since then, which plays videos mostly fine. Some other people with Radeon X-Series cards [have reported this problem]("http://www.ubuntuforums.org/showthread.php?t=202598").

So, anyone with a Radeon X-something is experiencing these or similar problems?

---

### Post by Phenz on 2006-12-19
Solution that worked for me:

I changed in my /etc/X11/xorg.conf

Option "OpenGLOverlay" "on"

To:
Option "OpenGLOverlay" "off"

Restarted X... still nothing... but after I killed the process "gnome-screensaver" and started it over in terminal... everything worked:)

---

### Post by pertti on 2006-12-19
> **Phenz said:**
> Solution that worked for me:

I changed in my /etc/X11/xorg.conf

Option "OpenGLOverlay" "on"

To:
Option "OpenGLOverlay" "off"

Restarted X... still nothing... but after I killed the process "gnome-screensaver" and started it over in terminal... everything worked:)

Wow, that solved the screensaver and screenlock problems! :D I didn't have to restart gnome-screensaver, though.

Sadly, Totem doesn't play video anymore :(. It doesn't work with neither of the three choices gstreamer-properties provides. I will continue to use MPlayer in the meantime. Do you have this problem too?

Thanks for you solution

---

### Post by Phenz on 2006-12-21
> **pertti said:**
> Wow, that solved the screensaver and screenlock problems! :D I didn't have to restart gnome-screensaver, though.

Sadly, Totem doesn't play video anymore :(. It doesn't work with neither of the three choices gstreamer-properties provides. I will continue to use MPlayer in the meantime. Do you have this problem too?

Thanks for you solution

Yes I had this problem also.... I just switched to xine-lib from gstreamer and have no problems:D

---

