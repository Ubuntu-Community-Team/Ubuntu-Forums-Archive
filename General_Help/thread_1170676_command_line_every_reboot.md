---
title: "command line every reboot"
date: 2009-05-26
forum: General Help
---

### Post by njb on 2009-05-26
Hello,

I want that command line to be run every reboot of my ubuntu PC

:KS Thank you

---

### Post by tdreyer1 on 2009-05-26
Can you elaborate please? Do you want to be able to reboot into a command line environment, or do you want a script to be run when your computer shuts down/starts up?

More info please!:D

---

### Post by upbeat.linux on 2009-05-26
Try this:

```
echo "false" | sudo tee /etc/X11/default-display-manager
```

---

### Post by tdreyer1 on 2009-05-26
> **upbeat.linux said:**
> Try this:

```
echo "false" | sudo tee /etc/X11/default-display-manager
```

...try this to get a command line only environment.

---

