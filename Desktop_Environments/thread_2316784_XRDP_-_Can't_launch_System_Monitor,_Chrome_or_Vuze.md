---
title: "XRDP - Can't launch System Monitor, Chrome or Vuze(Azureus)"
date: 2016-03-10
forum: Desktop Environments
---

### Post by spiritofcat on 2016-03-10
I've been running 12.04 for a number of years, using it as a torrent downloading and media server machine, serving a bunch of external hard drives to my local network to be accessed by windows machines and android devices.

I've just installed XRDP in the hope of being able to operate the machine remotely. I've followed guides on Griffon's IT Library, and managed to be able to connect on Unity, xfce4, or lxde.
However, while I can connect and operate most programs normally, I can't get System Monitor, Chrome or Vuze to launch in any of them.
Firefox works, and Thunderbird works, but Chrome is my preferred browser, and it's not much use as a torrent downloading machine if I can't access Vuze.

Any ideas?

Don't know if this has any impact on the situation, but the computer is still logged in and running both Vuze and Chrome locally. Perhaps they can't be run in two different sessions at the same time?

Is there a way to connect to the existing session on that machine instead of starting a new one for XRDP?

Edit: Just checked on the computer physically and I found a whole heap of chrome windows open, and system monitor too.
Looks like my attempts to launch worked, but they appeared on the physical session, not the remote one...?

[B]Tried logging out and leaving the computer sitting at the login prompt, then connecting with XRDP and that seems to have solved the problem.

I'd really like to be able to keep that computer logged in though, and access the same session remotely. Is that possible?[/B]

Edit: Looks like vino might offer the functionality I'm looking for.
I'm about to follow the tutorial here: [http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)

Edit: Yep, Vino does the job! Problem solved.

---

