---
title: "KDE4 Taskbar does now show up on start"
date: 2008-06-26
forum: Desktop Environments
---

### Post by vargadanis on 2008-06-26
Hi

I have just installed KDE4 using packages. I use 2 monitors in twinview. I used the nvidia-settings app to set up twinview. It worked till a reboot. I belive some settings got messed up and the taskbar or launchpad does not show up any more. I treid removing the entire KDE4 with --purge option and reinstall it but the same thing happened. Why is it? Or how can I solve the prob?

---

### Post by GeneralZod on 2008-06-26
> **vargadanis said:**
> Hi

I have just installed KDE4 using packages. I use 2 monitors in twinview. I used the nvidia-settings app to set up twinview. It worked till a reboot. I belive some settings got messed up and the taskbar or launchpad does not show up any more. I treid removing the entire KDE4 with --purge option and reinstall it but the same thing happened. Why is it? Or how can I solve the prob?

This will almost certainly be a problem with your Plasma config - it has an unfortunate tendency towards getting corrupted.

The only real way to solve it is to do the following from a terminal:

```

kquitapp plasma
rm $KDEHOME/share/config/plasma*
plasma

```

This will kill Plasma, remove the two Plasma config files, and restart Plasma.  Note that if you have made any customisations to your desktop e.g. adding widgets, re-arranging your panels etc, these will be lost.

---

