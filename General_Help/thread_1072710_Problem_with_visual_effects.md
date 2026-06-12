---
title: "Problem with visual effects"
date: 2009-02-17
forum: General Help
---

### Post by Pro$pect on 2009-02-17
Under the Visual Effects menu it allows me to switch from zero to extra, but when I restart my laptop it will freeze on the splash screen. I have to hit the power button for it to unfreeze and boot up, and when my desktop loads compiz won't be running because the settings have been switched back to none. How do I get it to stay on extra?

---

### Post by taurus on 2009-02-17
What kind of graphic card do you have and have you installed a driver for it?  Look in System -> Administration -> Hardware Drivers to see if you card is on the list.

---

### Post by Pro$pect on 2009-02-17
I have an nvidia 8400m gs with the 177 drivers installed, installing the 180 drivers right now...

---

### Post by Pro$pect on 2009-02-17
maybe I shouldn't have done that, awn isn't running after installing to 180

edit: after restart awn will run if I refresh compiz. But it is still switching to no effects when I boot up.

---

### Post by Pro$pect on 2009-02-17
I just realized that when I restart the settings manager, the effects changes from none to extra and awn will start up. How can I have ubuntu do this automatically at start up?

---

### Post by Pro$pect on 2009-02-17
I created the following script to run compiz at startup which keeps my settings on extra.

#/bin/bash
 sleep 10
compiz --replace

---

### Post by Pro$pect on 2009-02-17
it still freezes at the splash screen though...sometimes it works and sometimes it doesn't, it has to be from compiz.

---

