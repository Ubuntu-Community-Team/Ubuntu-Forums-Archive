---
title: "Broken: Settings &gt; Appearance &gt; Style"
date: 2013-10-06
forum: Desktop Environments
---

### Post by Buntu Bunny on 2013-10-06
I've been using the Greybird theme in Xfce 4.10 on Ubuntu 12.04. This morning when I booted up, I first noticed some of the panel icons had changed. The I realized the panel color and window title bars were a different color than greybird. Greybird is still highlighted in the settings manager, which won't change the theme no matter what I select. I discovered this is true for icons as well. Is anyone else having this problem? Better yet, any suggestions of how to fix it?

---

### Post by Buntu Bunny on 2013-10-07
This morning I booted my computer and everything was back to "normal," i.e. my originally chosen appearance and icon themes. I have no idea what happened: how and why they switched in the first place and how and why they switched back. And Settings > Appearance is no long frozen. Not sure what else to say except, yay.

---

### Post by Frogs Hair on 2013-10-07
I have seen this in the xfce session and it is due to th window manager crashing . Because I run different sessions I see this once in a blue moon. The following command or restarting usually solves the problem. ```
xfwm4 --replace
```

---

### Post by Buntu Bunny on 2013-10-07
> **Frogs Hair said:**
> I have seen this in the xfce session and it is due to th window manager crashing . Because I run different sessions I see this once in a blue moon. The following command or restarting usually solves the problem. ```
xfwm4 --replace
```

Frogs Hair, thank you! That's so logical that I don't know why it didn't occur to me, especially since I've had a few window manager problems recently. I'll keep all this tucked under my hat.

---

