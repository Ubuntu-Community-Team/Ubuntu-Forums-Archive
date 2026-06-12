---
title: "internet always requires manual connection"
date: 2007-11-02
forum: Desktop Environments
---

### Post by GlennW on 2007-11-02
I have a high speed cable connection to the internet. However, I must left click on the icon (upper right) and choose my connection. How can I set it up so that it connects upon startup? I'm quite the newb, having just installed Gutsy.

---

### Post by jpietari on 2007-11-03
Try System->Administration->Network then select your Wired Connection and unclick roaming or change settings to ensure you only have one connection selected.  I'm more or less guessing that this is the problem.

---

### Post by GlennW on 2007-11-05
Both eth0 and eth1 have roaming enabled. However, it won't allow me to disable the roaming. What gives with that?

This is what I have to select every time I want an internet connection. In the upper right hand part of the screen: 

[INDENT]Wired Network (Macronix, Inc. [MXIIC]MX987x5)[/INDENT]

There is another selection but it's some other obscure thing that doesn't work and besides, it's grayed out.

---

### Post by telic on 2007-11-05
> **GlennW said:**
> I have a high speed cable connection to the internet. However, I must left click on the icon (upper right) and choose my connection. How can I set it up so that it connects upon startup? I'm quite the newb, having just installed Gutsy.

Ever since Edgy, I found that I must disable *Network Manager*, so that my desktop PC will have automatic Internet connection via my Ethernet cable modem. My NIC also has the Macronix chipset.

Under *System -> Administration -> Network*, for the Wired Connection properties Configuration setting, I have selected *Automatic configuration (DHCP)* and disabled roaming.

Go to *System -> Preferences -> Sessions* and uncheck *Network Manager* in the *Startup Programs* tab. Then restart Gutsy.

Does this work for you?

---

### Post by GlennW on 2007-11-06
> **telic said:**
> Ever since Edgy, I found that I must disable *Network Manager*, so that my desktop PC will have automatic Internet connection via my Ethernet cable modem. My NIC also has the Macronix chipset.

Under *System -> Administration -> Network*, for the Wired Connection properties Configuration setting, I have selected *Automatic configuration (DHCP)* and disabled roaming.

Go to *System -> Preferences -> Sessions* and uncheck *Network Manager* in the *Startup Programs* tab. Then restart Gutsy.

Does this work for you?

It worked perfectly!! Thanks so much for your help.

---

