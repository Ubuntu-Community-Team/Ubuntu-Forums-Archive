---
title: "Faster Bootup?"
date: 2005-04-15
forum: Desktop Environments
---

### Post by Chris_Durham on 2005-04-15
What can I do to make my little Hoary system boot faster? There's a lot of things that seem to load up - some of which I don't need, like RAID drivers and things like that. Where can I go to examine these things closer and edit what it's doing during the process?

---

### Post by sakka on 2005-04-15
[QUOTE=Chris_Durham]What can I do to make my little Hoary system boot faster? There's a lot of things that seem to load up - some of which I don't need, like RAID drivers and things like that. Where can I go to examine these things closer and edit what it's doing during the process?[/QUOTE]
----------

^^^BUMP^^^ : re: RAID drivers

back to cake <
sakka

---

### Post by accuser on 2005-04-15
The kernel boots pretty quickly, but most of the boot up time is spent in the init scripts. Take a look in /etc/rcS.d and /etc/rc2.d. These two directories contain scripts that are executed on startup. /etc/rcS.d scripts on startup, /etc/rc2.d scripts when init enters run-level 2. Anything you feel is not necessary you can disable (IIRC) by removing the executable bit from the file:
```
$ sudo chmod -x <filename>
```
I would make sure you know how to rescue your system first in case you hose the init scripts. Have you got a Live CD handy?

DISCLAIMER: You do this at your own peril! :-)

---

### Post by Chris_Durham on 2005-04-15
Thanks. I'lll give that a try. We're looking at loading it on a bunch of 500 Mhz Dell GX100s for purposes of running RDesktop to hit a Windows Terminal Server. All we need is Network, Video, and Sound redirection. I've got it on a similarly-powered laptop right now and it takes about a minute-thirty to get to the login screen. We want to minimize this if we can.

---

### Post by Chris_Durham on 2005-04-15
[QUOTE=accuser]The kernel boots pretty quickly, but most of the boot up time is spent in the init scripts. Take a look in /etc/rcS.d and /etc/rc2.d. These two directories contain scripts that are executed on startup. /etc/rcS.d scripts on startup, /etc/rc2.d scripts when init enters run-level 2. Anything you feel is not necessary you can disable (IIRC) by removing the executable bit from the file:
```
$ sudo chmod -x <filename>
```
[/QUOTE]

When I try to do this I get an error saying : Could not open the file "/etc/rc2.d" the file you are trying to open is not a regular file.

I'm doing this from a terminal window using gedit. Is there another way I should try?

---

### Post by Chris_Durham on 2005-04-15
On second glance, I can't even find these files when I browse for them.

---

### Post by Chris_Durham on 2005-04-15
Nevermind. Found them - Folders

---

### Post by Chris_Durham on 2005-04-15
Next Question. Can anyone point me to where I can figure out what each of these does?

---

