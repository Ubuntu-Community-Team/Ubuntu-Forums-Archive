---
title: "resolution settings broken - command line fix?"
date: 2008-10-21
forum: Desktop Environments
---

### Post by jangari on 2008-10-21
I've been fiddling around with the screen resolution settings to get my22" LCD working at the right resolution, but I've inadvertently selected a setting that it doesn't support, somehow.

I'd disabled the laptop monitor already as that was just causing issues, so now when I log into X, I just get this message straight from the monitor saying 'input not supported' and nothing shows up on the laptop monitor.

I've tried reconfiguring xorg.conf, but that didn't help, and I've researched some other fixes, such as xRandR, but that didn't do anything either. 

I can log in to tty1, so I need to alter the screen resolution settings from there. Even if I re-enable cloned output, it'll then allow me to see what I'm doing in X so I can get it back to how it was.

Can I revert the resolution settings to the default somehow using a terminal?

---

### Post by overdrank on 2008-10-21
> **jangari said:**
> I've been fiddling around with the screen resolution settings to get my22" LCD working at the right resolution, but I've inadvertently selected a setting that it doesn't support, somehow.

I'd disabled the laptop monitor already as that was just causing issues, so now when I log into X, I just get this message straight from the monitor saying 'input not supported' and nothing shows up on the laptop monitor.

I've tried reconfiguring xorg.conf, but that didn't help, and I've researched some other fixes, such as xRandR, but that didn't do anything either. 

I can log in to tty1, so I need to alter the screen resolution settings from there. Even if I re-enable cloned output, it'll then allow me to see what I'm doing in X so I can get it back to how it was.

Can I revert the resolution settings to the default somehow using a terminal?
Hi and if you are using Hardy you may try and boot into recovery mode which is usually the second choice from the grub and use the xfix option.

---

### Post by jangari on 2008-10-21
> Hi and if you are using Hardy you may try and boot into recovery mode which is usually the second choice from the grub and use the xfix option.
Thanks, I've tried that too, I forgot to mention. No change at all.

---

### Post by jangari on 2008-10-21
Odd. I just tried it (xfix in recovery mode) again with the monitor removed completely, and this time it worked! Thanks.

---

