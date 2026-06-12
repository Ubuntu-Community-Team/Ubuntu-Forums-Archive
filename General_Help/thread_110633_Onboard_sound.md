---
title: "Onboard sound"
date: 2005-12-31
forum: General Help
---

### Post by chrisndebb on 2005-12-31
Just installed another motherboard, ASUS A7S8X-MX, and want to use onboard sound which is ADI AD1888 AC '97. Ubuntu 5.10 doesn't seem to want to detect it. Anybody have any similar situations? I found where Hoary will use ADI 1881.

---

### Post by HanZo on 2006-06-29
had exactly the same issue. Have a A8U-X mobo with the same soundchip.
Bored of fiddling around with ubuntu I tried Suse 10.1 same problem... but now I found something... there is one thing where Suse beats Ubuntu by far: confi utils (very good for lazy ppl like me) Yast gives me the option to turn on two "workarounds" for a) problematic interrupts on some motherboards (buggy irq) and b) problematic codec semaphor (bool) (sorry translating this from german so may not be 100% accurate). know what, now everything works fine.. card is detected and sounds ok! looked at the driver it is using it is detected as M5455 PCI AC-LINK Controller Audio device using the snd-intel8x0 driver module.
hope this can be any help... unfortunately I don't know how to activate these workarounds in dapper...

---

