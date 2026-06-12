---
title: "Desktop Effects not working???"
date: 2008-01-15
forum: Desktop Effects &amp; Customization
---

### Post by Josh_NC on 2008-01-15
I have a ATI Radeon (I forget what its number is). It has 128megs of ram. 

I installed it via the Restricted Drivers Manager and everything seems to work.

But when I go to enable the Desktop effects, it says, "The Composite extension is not available"

Any idea how I can get this to work???

---

### Post by divague on 2008-01-15
you have to install xserver-xgl, so you can use the effects

---

### Post by Josh_NC on 2008-01-15
> **divague said:**
> you have to install xserver-xgl, so you can use the effects

I already did...

---

### Post by ByKeLaO on 2008-01-15
Have you tried ```
sudo apt-get install compiz
```?

---

### Post by FuturePilot on 2008-01-15
> **Josh_NC said:**
> I already did...

Did you log out and log back in? You need to do this in order for X to restart itself and XGL to be initiated.

---

### Post by Josh_NC on 2008-01-15
> **FuturePilot said:**
> Did you log out and log back in? You need to do this in order for X to restart itself and XGL to be initiated.

Yes, I already did. Its not working. Its still giving me the same message.

---

