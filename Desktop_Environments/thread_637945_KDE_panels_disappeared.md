---
title: "KDE panels disappeared"
date: 2007-12-11
forum: Desktop Environments
---

### Post by Gyatak on 2007-12-11
Hi all,

I turned on my computer this morning and my main and universal sidebar panels had disappeared in KDE. I've tried looking to see if they had somehow slid off the page, but can't find them. I ran kcontrol, and verified that they're both there in the panels setting. I even formatted them as LARGE, but they still didn't appear. I've tried restarting, no luck. I also followed someone's advice to run

```
dcop kicker kicker restart
``` 

but get the message **call failed**.

I'm running Gutsy with Compiz Fusion and all my upgrades are up to date. Needless to say, this is somewhat crippling.

Any ideas?

---

### Post by Gyatak on 2007-12-11
Additional note. I'm running advanced window manager, and noticed that the system tray apps (such as battery monitor, bluetooth, adept notifier, and klipper) are now appearing there, which they don't normally do.

---

### Post by GeneralZod on 2007-12-11
Try ALT+F2 and enter:

```

kicker

```

---

### Post by Gyatak on 2007-12-11
That did the trick. Thanks!

I wonder why this suddenly stopped loading automatically :???:

---

### Post by GeneralZod on 2007-12-11
> **Gyatak said:**
> That did the trick. Thanks!

I wonder why this suddenly stopped loading automatically :???:

It may have crashed on startup, but usually you'd see Dr Konqi in such a situation.

One of life's little mysteries, I guess :)

---

