---
title: "Nvidia X Server resets after shutdown"
date: 2021-01-18
forum: Desktop Environments
---

### Post by nhorton04 on 2021-01-18
Hello,

I've searched this problem extensively and found lots of other people dealing with the same issue, but no suggested fixes have worked. 

I use two monitors. One of the monitors needs underscan set to 40 for everything to be visible on the screen. At first, I was unable to get this to persist after shutdown. Recently I figured out how to save the configuration in .nvidia-settings-rc , and now the 40px underscan persists through reboot!

However, now there's something new I need to fix at every bootup. The layout of the screens is defaulted to have a gap between them, so when I try to maximize windows on the underscanned monitor it doesn't work. I need to manually open Nvidia X Server settings and drag the screen over on the layout area.

There doesn't seem to be any field in the configuration file to adjust the layout...can anyone help?  Layout Gap----->[ATTACH=CONFIG]287764[/ATTACH]

---

### Post by &amp;KyT$0P# on 2021-01-18
Which desktop environment are you using?  Try going into your desktop environment's display settings and doing something there to ensure it has saved the same configuration as you made in Nvidia settings?

---

