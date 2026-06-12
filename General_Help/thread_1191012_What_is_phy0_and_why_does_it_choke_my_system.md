---
title: "What is phy0 and why does it choke my system?"
date: 2009-06-18
forum: General Help
---

### Post by bryceowen on 2009-06-18
I'll be using my system just fine with no problems, but every 60 seconds or so, I get a hiccup that causes the mouse to freeze, scrolling interrupts and just plain annoys me. Conky and top both show 'phy0' tying up about 40% of the cpu when it happens.

What exactly is phy0, why is it doing this and how can I stop it?

---

### Post by bryceowen on 2009-06-18
I suspect the problem might be related to my wireless. Looking in dmesg, I see line-after-line of:
```

[13061.823766] ath5k phy0: noise floor calibration timeout (2442MHz)

```
Ath5k would suggest the Atheros wireless adapter in my EEE. I will disable wireless next boot and see if I still have the same hiccups.

I didn't need to reboot. I simply turned wireless off in NM-Applet and the problem went away. It would also seem this is a known bug with the ath5k driver, but it still hasn't been fixed.

---

### Post by t4thfavor on 2009-06-18
Sounds like a bad driver for your WIFI card, your post says ath5k, but I have really only seen Broadcom ones with phy0 as the name of the card.


I have read though that the new atheros drivers are less stable than the old ones (too bad you can't use the old ones anymore)

And if it is Broadcom, you better off getting another card than fighting that battle.

Sorry I couldn't be of more help.

---

### Post by bryceowen on 2009-06-18
No problem. Thanks for the reply, though. As I said in my edit above, it is a known problem with the ath5k driver. No fix in sight, short of using the ath_pci driver.

> **t4thfavor said:**
> Sounds like a bad driver for your WIFI card, your post says ath5k, but I have really only seen Broadcom ones with phy0 as the name of the card.


I have read though that the new atheros drivers are less stable than the old ones (too bad you can't use the old ones anymore)

And if it is Broadcom, you better off getting another card than fighting that battle.

Sorry I couldn't be of more help.

---

