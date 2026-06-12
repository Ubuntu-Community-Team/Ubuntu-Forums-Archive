---
title: "Cannot Construct Test Pipeline to ALSA"
date: 2006-01-10
forum: Desktop Environments
---

### Post by tig4 on 2006-01-10
Hey guys,

Just reinstalled the OS without my PCI Soundcard to see if just having the onboard 5.1 soundcard would work better. 

MOBO: Asus A7N8X-D
5.1 Surround

Anyways, before the reinstall everything worked fine, however, now I cannot select the ALSA System as my sound, it gives me the error, "Cannot Construct Test Pipeline to ALSA"

And I have no sound coming from the speakers, any ideas?

Thanks,

Tig

---

### Post by tig4 on 2006-01-10
tigfour@blackbox:~$ lspci -v | grep -i audio
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia audio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

---

### Post by tig4 on 2006-01-11
Anyone?

---

### Post by mcduck on 2006-01-11
Try 'killall esd' first.

also, there are some nice HowTo's in this forum about multiple sounds using ALSA, try to search for more info. Or try this one: [http://www.ubuntuforums.org/showthread.php?t=44753&highlight=alsa+multiple+sounds]("http://www.ubuntuforums.org/showthread.php?t=44753&highlight=alsa+multiple+sounds") (it's not the howto that I used with my A7N8X-E, but it's supposed to work with nForce2 MB's)

---

