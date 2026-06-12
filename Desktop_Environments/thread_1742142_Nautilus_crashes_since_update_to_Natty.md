---
title: "Nautilus crashes since update to Natty"
date: 2011-04-28
forum: Desktop Environments
---

### Post by atundel on 2011-04-28
Hello everyone. Since I have updated last night from maverick to the latest beta of natty narwal, I'm having a lot of trouble getting Nautilus (desktop included) to work.

It seems to crash since the very start as when I turn off the computer, the message of "force exit" appears.

Any suggestions?

Thanks in advance. :KS

---

### Post by deprieto on 2011-05-07
Hi,

I've been through a lot of forums, inconclusive bug reports  and still have the very same problem, without soultion. It seems to be  that only a small minority is having this BIG problem, even in the *stable* version of Natty. Could that be  possible?

As a workaround, in the meanwhile, I've been using Thunar, for there is no immediate hope for Nautilus.

:sad:

---

### Post by deprieto on 2011-05-08
I've found a better solution, that actually makes Nautilus work, and make the computer feel a lot snappier. The solution involves getting rid off COMPLETELY of Ubuntu One.

Deleting configuration files, like rm -r ~./gnome, or reinstalling, didn't work.

An observation in top, revealed that the process **ubuntuone-syncdaemon**, which is used by Nautilus for all the Ubuntu One stuff,  was taking [COLOR=Red]**more than 80% CPU usage**[/COLOR].

I couldn't kill the process, so I went radical and decided to remove all of Ubuntu One, by typing in the terminal.
[INDENT]sudo apt-get purge ubuntuone-client
[/INDENT]Suddenly, all of the windows I tried to open previously sprung open, and I could browse. The computer also felt faster after that, even faster than prior to the upgrade.

---

### Post by sebvogel on 2011-06-03
@deprieto: thank you for the solution - I just had the same problem and purging the ubuntu-one client did work perfectly for me!

---

