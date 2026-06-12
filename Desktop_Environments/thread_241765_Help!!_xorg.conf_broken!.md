---
title: "Help!! xorg.conf broken?!?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by goatflyer on 2006-08-22
While attempting to perform the solution suggested in this thread...

[http://www.ubuntuforums.org/showthread.php?t=237967](http://www.ubuntuforums.org/showthread.php?t=237967)

... I have lost my ability to start X

All I had done was remove the "1600x1200" option from all the screen-depths. (Fortunately I made a backup of the xorg.conf file).

Nothing happened.  I ran...

sudo dpkg-reconfigure -phigh xserver-xorg

...selected my resolution, and the tried to startx

It fails saying no screen detected
/var/log/Xorg.0.log says (EE) No device detected.

yet lspci shows my nvidea card

I restored the xorg.conf from backup, still the same error message - no screen detected.

I boot from old LiveCD, and screen and everything comes up like normal.

Yet rebooting back to my installed Ubuntu fails to start X

Help! What do I do?

---

### Post by ShamusPatt on 2006-08-22
You're not alone.Check some of the other threads e.g. "http://www.ubuntuforums.org/showthread.php?t=241254". Basically, you need to back out the update xserver-xorg-core to before the update to it yesterday.

---

### Post by K.Mandla on 2006-08-22
Don't worry. That bug got a bunch of us. You should be able to update again and get a [corrected version]("http://packages.ubuntu.com/dapper/x11/xserver-xorg-core") of xserver-xorg-core. I updated about two hours ago and got a working version.

If not, you might try the ideas [here]("http://www.ubuntuforums.org/showthread.php?t=241254").

---

### Post by asplode on 2006-08-22
> **K.Mandla said:**
> Don't worry. That bug got a bunch of us. You should be able to update again and get a [corrected version]("http://packages.ubuntu.com/dapper/x11/xserver-xorg-core") of xserver-xorg-core. I updated about two hours ago and got a working version.

If not, you might try the ideas [here]("http://www.ubuntuforums.org/showthread.php?t=241254").

Did it get the ugly little computer that could??! :frown:

---

