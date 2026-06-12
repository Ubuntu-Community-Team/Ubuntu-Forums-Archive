---
title: "Help Stuck on &quot;hotplug subsystem&quot;"
date: 2005-08-12
forum: Desktop Environments
---

### Post by jefffro on 2005-08-12
I have just completed the first set in installing ubuntu, right before i restart it tells me to take the install disk out, so i do that, and then it runs through a couple of checks (..........ok) and when it gets to starting Hotplug subsystem, it just sits there and doesnt do anything, I have tried switching the instal CD's but I keep getting the same thing. Please Help!
Jeff

---

### Post by Gezzer on 2005-08-12
unsure if this of any help but u can try it

unplug all usb devices from the system
start the sytem up and see if the hot plug system installs

then plug your usb devices in
its worth a try ...

---

### Post by jefffro on 2005-08-12
Nope didnt help, Thanks though
Jeff

---

### Post by cwaldbieser on 2005-08-12
[QUOTE=jefffro]Nope didnt help, Thanks though
Jeff[/QUOTE]
Does hitting CTRL-C skip that step during the boot up?

---

### Post by jefffro on 2005-08-12
Yup! That did it, thanks alot! What all did that service do?
Jeff

---

### Post by cwaldbieser on 2005-08-12
[QUOTE=jefffro]Yup! That did it, thanks alot! What all did that service do?
Jeff[/QUOTE]
The hotplug system normally controls things like telling the operating system when you plug in a USB drive or a digi-cam.  You can think of it as "plug-n-play".

I had a problem like that once when I wrote my own hotplug script and I forgot to run it in the background.  When the system boots up, it fires off all the hotplug scripts as part of the initialization, but because my script didn't wait in the background, it was hanging the system.

---

