---
title: "Disable sound in XFCE?"
date: 2005-08-31
forum: Desktop Environments
---

### Post by french_mullet on 2005-08-31
This is kind of the opposite problem that most people have, but I want to disable sound in xfce.

For some reason, xfce-panel and the mcs session manager process open /dev/snd/controlC0 device.  I thought perhaps it was a mixer app or something in the panel, but there is nothing like that configured.

The reason I want to do this is because when my laptop comes out of suspend, the sound is borked.  To fix it, I have to rmmod and modprobe the soundcard module.  In order to do this I have to kill xfce-panel and the mcs manager.   

Needless to say, this is big pain in the behind.  So I'm looking for a way of preventing XFCE from using the sound devices.

---

### Post by weekend warrior on 2005-09-01
There's an [XFSound module](http://seth.positivism.org/man.cgi/1/xfsound) that you might look into. It's worth asking about in the XFCE forums:

[http://forum.xfce.org/](http://forum.xfce.org/)


HTH

---

