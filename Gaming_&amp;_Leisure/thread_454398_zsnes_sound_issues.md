---
title: "zsnes sound issues"
date: 2007-05-25
forum: Gaming &amp; Leisure
---

### Post by band-aid on 2007-05-25
Under windows, my sound is fine in zsnes. I can play super mario RPG with very little issue in this area. Under ubuntu, however, my sound is garbled and pops and cracks something awful. Any idea why it would be different? Its the same rom and same emulator.

---

### Post by po0f on 2007-05-25
band-aid,

```
$ sudo apt-get install libsdl1.2debian-oss
```

---

### Post by BigSilly on 2007-05-25
That did the trick for me too. I had the same problem you describe, and this worked. Just recommended this procedure to a friend funnily enough.

---

### Post by band-aid on 2007-05-25
It appeared that this worked for a bit (about 2 minutes) and now its back to garbled. Also, it removed the debian libsdl alsa library, is this something to worry about?

EDIT: I think it may screw up when I move the window around a lot, is there a equivalent command to /etc/init.d/networking restart to restart your sound?

---

### Post by Chris S. on 2007-05-25
Try increasing the ZSNES sound sampling rate to 48000Hz.

If you still get crackling, then try to apt-get install alsa-oss (I think that's the right package), and use the 48000Hz sampling rate.  This fixed the crackling for me.  You'd probably need the libsdl-alsa package instead of the oss package.

You may need to close and reopen ZSNES for the settings to take.

---

