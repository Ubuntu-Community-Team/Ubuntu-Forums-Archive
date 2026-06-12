---
title: "how restarting Alsa or making hotplug work?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by sonium on 2006-07-02
Hi, my USB soundcard sometime stops working. Either after disconnecting an reconnecting (hotplug doesn't seem to work) or sometimes when I switch on my speakers (I think this produces something like a voltage peek that kills the card).

In Breezy the sollution then was "sudo /etc/init.d/alsa restart". But now we only have alsa-tools which doesn't seem to affect alsa directly. But when I shut down Ubuntu alsa starts working again suddenly (I hear the initialisation noise and the logoff sound).

So how can I either make hotplug work correctly or restart the whole alsa system?

edit: Another problem that may be related to hotplug is that lsusb does not work (it simply hangs up)

---

