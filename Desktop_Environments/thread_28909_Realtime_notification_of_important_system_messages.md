---
title: "Realtime notification of important system messages?"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Alexandr on 2005-04-22
It is possible abandon to use postfix for delivery of messages from anacron and other daemons to local mailbox?

Want to see all these messages (and critical iptables messages) a real-time mode in splash-window or small information icons (not root-tail :) ).

Home desktop system.

Thanks.

---

### Post by andvaranaut on 2005-04-22
Hi Alexandr

Although I think that this is not possible by now, this is being actively worked on by the Linux desktop community at large.

The main obstacle in getting all this to work is that applications often use different (ie. incompatible) ways to signal their events. One uses syslog, the next sends mail, the next uses a popup, etc. ad nauseam. Of course, getting every application to work the same way is a pain. That is why a common framework for notifications is needed.

There are a few possibilities for this. freedesktop.org, as well as Gnome (and likely KDE rather soon) favor one called D-BUS. D-BUS is a message bus: whenever an application has something to notify, it emits a D-BUS signal. The signal is then received by any application that is waiting for it and acts accordingly.

For example, (correct me if I'm wrong) when you plug a USB pendrive in, a component called HAL sends a D-BUS message. This D-BUS message is then received by the desktop, which mounts and shows your keychain. D-BUS serves as the communication channel between the components.

I think that the kind of notifications that you want will arrive when most application developers support some kind of D-BUS 'logging message'. An application on the desktop would listen to these messages and show alerts accordingly. Seems like a cool project for me ;)

That being said, having an e-mail (also) sent is nice, because you might not be around to see the notifications ;)

Cheers

---

### Post by Alexandr on 2005-04-22
Thank you for answer. Nearly all clear.

[QUOTE=andvaranaut]
That being said, having an e-mail (also) sent is nice, because you might not be around to see the notifications ;)
[/QUOTE]
Probably, this correct.  :) 
In addition I has found discussion in "Ubuntu Development Mailing List":

[http://ubuntuforums.org/showthread.php?t=14517&highlight=MTA+ubuntu+deskop](http://ubuntuforums.org/showthread.php?t=14517&highlight=MTA+ubuntu+deskop)

Maybe this is interesting?

Good luck!

P.S.
Apologize for my english. In school and institute I in general-that study german, additionally this there was long ago. ;) 
And I translate from english to russian well, but from russian to english... as this is seen. :)

---

### Post by andvaranaut on 2005-04-22
> **Alexandr]Thank you for answer. Nearly all clear.[/quote]
You're welcome :)

> 
In addition I has found discussion in "Ubuntu Development Mailing List":

[http://ubuntuforums.org/showthread.php?t=14517&highlight=MTA+ubuntu+deskop](http://ubuntuforums.org/showthread.php?t=14517&highlight=MTA+ubuntu+deskop)

Maybe this is interesting?

What is described here is rather nice and seems to solve your concerns, so you (and many others, me included  said:**
> P.S.
Apologize for my english.
You make yourself perfectly understood, so there's nothing to apologize for ;)

Have a nice day!

---

