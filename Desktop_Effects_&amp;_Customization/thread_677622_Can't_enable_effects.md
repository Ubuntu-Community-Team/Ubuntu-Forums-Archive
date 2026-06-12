---
title: "Can't enable effects"
date: 2008-01-25
forum: Desktop Effects &amp; Customization
---

### Post by sporkubus on 2008-01-25
When I try to enable Normal or Extra effects in Appearance Preferences, I get this error: The Composite extension is not available. What can I do to fix this?

---

### Post by Cresho on 2008-01-25
First off, what graphics card are you using.  Secondly, Have you installed drivers?

---

### Post by sporkubus on 2008-01-25
I'm not actually sure what graphics card I have... whichever one is in this Aspire 5100 laptop, I guess. Is there some way to check? And yes, I installed and enabled the restricted drivers that were automatically downloaded.

---

### Post by FuturePilot on 2008-01-25
This will show you you're graphics card
```
lspci | grep VGA
```

---

### Post by sporkubus on 2008-01-25
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

---

### Post by FuturePilot on 2008-01-25
I'm betting you need XGL
```
sudo apt-get install xserver-xgl
```
Log out and log back in. That should get it going.

---

### Post by sporkubus on 2008-01-25
That worked. Thanks!

---

