---
title: "Fluxbox sound card configuration"
date: 2011-04-13
forum: Desktop Environments
---

### Post by aerofly5 on 2011-04-13
I have 3 sound cards (one for the HDMI on my graphics card, one on a PCI bus and an onboard) and currently the amixer default is my PCI bus and the alsa (?) default is the onboard (which I want to play sound through). This is a problem because I programmed in a keyboard shortcut so that on event Ctrl+Down/Up it would execute an amixer command that changed the master volume. But, its changing the master volume for the PCI card, which doesn't even have any jacks plugged into it. Is there an extra switch I can use for amixer or a way to change the default?

---

### Post by aerofly5 on 2011-04-13
I used the --card [card number] switch to fix it

---

