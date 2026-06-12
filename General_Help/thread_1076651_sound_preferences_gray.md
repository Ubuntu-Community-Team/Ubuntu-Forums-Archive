---
title: "sound preferences gray"
date: 2009-02-21
forum: General Help
---

### Post by steigerjb on 2009-02-21
I am trying to set a Ubuntu startup sound. I have none :( I went to

System-Preferences-Sounds

but the sound tab is grayed out. See screenshot:

[http://i44.tinypic.com/29g0s1v.png]("http://i44.tinypic.com/29g0s1v.png")

Why is it gray? How do I fix?

Thanks in advance.

and P.S. - Why doesn't my 8.10 have the USB Creator Software?

---

### Post by steigerjb on 2009-02-22
nevermind, problem solved

---

### Post by steigerjb on 2009-03-06
just in case someone has the same problem as me. This worked for me:


"Open a terminal and type *sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2*. This will purge any custom configurations that you've made, and any hand-compiled modules that you've built, and restore your sound stack to the "Official" Ubuntu core. You can also do this as two separate steps: *sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils* and then *sudo apt-get install linux-sound-base alsa-base alsa-utils* , but this may result in some other packages which depend on the sound-base and alsa-utils from being removed, such as gdm and ubuntu-desktop. If this happens, then do *sudo apt-get install gdm ubuntu-desktop*

I did ALL of the codes, in order. Make sure you do the sudo apt-get install gdm ubuntu-desktop

):P

---

