---
title: "Keeping GTK themes and icon packs separate between desktop environments"
date: 2022-04-27
forum: Desktop Environments
---

### Post by picklemorty282 on 2022-04-27
Hello,

I recently installed the KDE Plasma desktop environment alongside GNOME.

When I apply an icon pack and GTK theme on KDE, it is also applied on GNOME. This is a frustrating problem.

Can someone help me on how to keep icon packs and GTK theme configurations separate between desktop environments?


Thanks in advance.

---

### Post by DuckHook on 2022-04-27
Please read the link in my sig: The Best 'buntu Flavour

It explains why mixing DE's is bound to cause problems and should be avoided.

Consider what you are asking in the context of what you have done:

You've basically done the equivalent of mixing two sets of LEGO parts together, then asked for each set to magically keep itself segregated from the other. This is neither fair nor possible.

If you want two different DEs that won't step on each other's toes, then install them as two distinct OSes in a dual boot setup. That is the only way to stop each DE from clobbering the other.

A further option is to run one DE as a VM within the other. I run multiple VMs in just this way: GNOME as my host, then half a dozen other flavours as guests.

---

### Post by picklemorty282 on 2022-04-28
I just need the icon and theme packs to be separate. Software related, it's fine

---

### Post by DuckHook on 2022-04-28
It's the icons, fonts and themes where many of the problems show up. Apps tend to be okay. Sometimes, the incompatibilities are very subtle. Hard to even trace back to the presence of multiple DEs.

Some people who stick to the defaults don't have problems with mixed DEs. It depends on how much you tend to customize. It's also unpredictable: some aspects are okay while others are not. Future upgrades will unveil further incompatibilities that don't show up for now. Some problems don't show up until you do something uncommon. Consider: you are mixing config files for basic GUI functions. Aside from the clobbering, if two similar configs exist, which one is the system supposed to use?

Speaking practically, I don't know how to help you. Mixing DEs is something that I strictly avoid, so I have no test bed to experiment on.

---

### Post by Frogs Hair on 2022-05-04
It may be possible if you create a new user with a different name for the KDE environment and only apply icon or GTK themes installed to a new .icons and .themes folder created in the home directory. Multiple desktop environments tend to get bloated and messy due to duplicate applications and they can be difficult to remove without leaving cruft on your system.

---

