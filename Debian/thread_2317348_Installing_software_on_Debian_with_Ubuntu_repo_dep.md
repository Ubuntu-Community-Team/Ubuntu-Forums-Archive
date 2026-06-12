---
title: "Installing software on Debian with Ubuntu repo dependencies?"
date: 2016-03-15
forum: Debian
---

### Post by lewdposter on 2016-03-15
Thanks

---

### Post by Frogs Hair on 2016-03-15
Moved to *Other OS/ Debian*

---

### Post by arochester on 2016-03-16
The usual Debian advice is NOT to add applications from other Distros because it might break your system.

Emphasis on "might". If you know how to deal with a break and have an adequate backup then adding something "might" be O.K.

[https://wiki.debian.org/DontBreakDebian/](https://wiki.debian.org/DontBreakDebian/)

That said, can you tell us exectly what you want to add?

---

### Post by T.J. on 2016-04-27
> **lewdposter said:**
> What is usually done in the case of just having a debian base and wanting software off the ubuntu software center?  i.e downloading the program itself, and then finding a solution to resolve dependencies.
Thanks

Well, I normally do not bother with old threads, but just in case the original poster is still interested.  One could always use dget and the .dsc file to download the source from the Ubuntu repository and build it against Debian.

[https://wiki.debian.org/SimpleBackportCreation](https://wiki.debian.org/SimpleBackportCreation)

If you aren't into hacking your own port, then I would suggest using something like debootstrap.

[https://wiki.debian.org/Debootstrap](https://wiki.debian.org/Debootstrap)

The really lazy way is a container or VM.

---

