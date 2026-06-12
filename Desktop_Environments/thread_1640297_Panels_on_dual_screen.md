---
title: "Panels on dual screen"
date: 2010-12-07
forum: Desktop Environments
---

### Post by flopin on 2010-12-07
Hello,
i am using kubuntu 10.10 and i have noticed this anoying behaviour:

I have dual screen setup with my laptop screen being primary and the external display secondary. I have added new panel to the secondary screen (with application launcher, taskbar and some other widgets), which is working fine. But, when I start the laptop without the external display, both panels are displayed on the primary (laptop) screen overlaying each other and making them both quite impossible to use. A always have to remove one of them after connecting external display create one again.

Is there any way to make the panel stay fixed (or not to display) on the secondary sreen, no matter if the external display is connecter or not? Or should i submit this as a bug/feature request?

Thanks

---

### Post by robbie d on 2010-12-07
I think that you might have to disable the second monitor before shutting down the laptop. Only a guess, but the behaviour with dual monitor setups to me is still a long way behind other OSs

---

### Post by flopin on 2010-12-08
Tried, it does not work. After start without external display, the panel is back on primary.

Since it seems it is not possible do it simple way, i have this idea:

Isolate config file of kde, where the iformation about panels are located, then create one for dual screen layout (two panels) and one for single screen layout (single panel). Then create a boot script, which will determine if the external is connected and load appropriate config before starting kde. It wont work for hot (un)plugging monitor, but better than nothing...

---

