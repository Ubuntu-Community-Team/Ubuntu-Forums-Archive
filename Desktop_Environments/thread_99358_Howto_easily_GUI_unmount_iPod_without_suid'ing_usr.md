---
title: "Howto easily GUI unmount iPod without suid'ing /usr/bin/eject?"
date: 2005-12-05
forum: Desktop Environments
---

### Post by plcarvalho on 2005-12-05
Any ideas?

Setting suid bit on /usr/bin/eject works but's that a disaster waiting to happen...

(yes, paranoid by default, that's me :) )

PS: Just to thank you all: developers, users, and all who made possible this wonderful distribution and friendly community. Thank you so much.

---

### Post by Gray. on 2005-12-05
Don't you just right-click the IPOD on the desktop and unmount it that way?

---

### Post by astoltz on 2005-12-05
[QUOTE=Gray.]Don't you just right-click the IPOD on the desktop and unmount it that way?[/QUOTE]
That's been discussed lots [here]("http://ubuntuforums.org/showthread.php?t=56515") and others.

As far as ejecting, I've had inconsistant results.  With my iPod (3G), I can eject as a normal user and all is well.  With my daughter's (mini) using the eject command throws an error (sorry, I can't remember exactly what) but I think it still works - the "Do Not Disconnect" goes away.  In both cases, ejecting as root (sudo eject ipod) works without errors.

Not exactly what you're looking for, I know, but thought it might help.

---

### Post by plcarvalho on 2005-12-05
[QUOTE=Gray.]Don't you just right-click the IPOD on the desktop and unmount it that way?[/QUOTE]

I wish. If I do that I get an eject error box:

Unable to eject media
eject: unable to eject, last error: Invalid argument

I can make that error box go away by suid'ing /usr/bin/eject (sudo chmod +s /usr/bin/eject) but that's a security risk I would like to avoid if possible.

Thank you.

---

### Post by plcarvalho on 2005-12-05
[QUOTE=astoltz]
As far as ejecting, I've had inconsistant results.  With my iPod (3G), I can eject as a normal user and all is well.
[/QUOTE]

Hummm... interesting... Mine's a 4G Photo iPod. 
Does that mean latest generation iPods can't be ejected as a normal user? 

Maybe something to do with udev permissions... Anyone?

[QUOTE=astoltz]
Not exactly what you're looking for, I know, but thought it might help.[/QUOTE]

I think it did... I will dig through udev docs now. ;)

---

### Post by astoltz on 2005-12-05
[QUOTE=plcarvalho]Maybe something to do with udev permissions... Anyone?[/QUOTE] That's a thought.  When I get home, I'll have to check how the device node gets created for each of the ipods.

I was thinking it had something to do with apple's firmware - but that was just a hunch.

---

