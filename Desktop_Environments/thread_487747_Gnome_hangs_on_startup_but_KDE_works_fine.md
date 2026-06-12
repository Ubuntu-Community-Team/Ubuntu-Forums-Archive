---
title: "Gnome hangs on startup but KDE works fine"
date: 2007-06-29
forum: Desktop Environments
---

### Post by beefcake on 2007-06-29
Hi,
I've installed Ubuntu 7.04 (Feisty) on an HP Pavilion zv5000 laptop, with XP Pro on a second partition. The installation process runs smoothly, but when I start the new system, Ubuntu hangs as soon as I enter my username and password. On the other hand, if I install KUBUNTU Feisty (NOT Ubuntu), the OS works without any problems. I cannot seem to figure out the difference between Gnome and KDE that's making one work on my system and not both. Incidentally, I changed the boot options at the boot loader menu as follows, without any effect:
added noapic nolapic acpi=off pci=noacpi to the kernel /... quiet ro splash line, but that didn't work either.

I'd really appreciate it if someone can help me out with this problem. Please let me know if you need further information to resolve this issue. Thanks in advance.

---

### Post by deepclutch on 2007-07-01
post the error message and also ur ~/.xsession-errors(last  lines)

---

### Post by beefcake on 2007-07-01
Ubuntu WORKS! It turns out that putting the following two parameters in ubuntu's boot option (in the kernel line) does the trick:

noapictimer irqpoll

Thanks anyways for your suggestion, deepclutch.

---

### Post by OzzyFrank on 2007-07-01
Well, my Gnome is totally screwed, and Openbox became a mutated mess after I loaded Nautilus (became like my Gnome desktop but without the panels). A link to my post is below detailing all the weirdness that's made Ubuntu pretty much useless. I didn't think to log into a KDE session (well, thought that would probably be worse if Openbox couldn't handle the Metacity ballsup since the Compiz upgrade). But yeah, as far as I could see, my Kubuntu desktop works fine.

[http://ubuntuforums.org/showthread.php?t=489206](http://ubuntuforums.org/showthread.php?t=489206)

I've never had any luck using boot options to fix any error, but will try those 2. Somehow I think it has more to do with screwy Compiz files affecting Metacity and Gnome in general. Hope I can find an answer soon!

[EDIT: I can confirm that the "noapictimer irqpoll" boot options work for me too! Gnome seems to work as usual, with no error messages. Still, I've seen in action a really good reason to install the Kubuntu desktop, even if you're only going to use Gnome]

---

