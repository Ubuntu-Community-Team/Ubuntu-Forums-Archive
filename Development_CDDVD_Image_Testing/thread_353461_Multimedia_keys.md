---
title: "Multimedia keys"
date: 2007-02-04
forum: Development CD/DVD Image Testing
---

### Post by lvanderree on 2007-02-04
The multimedia keys of my Logitech Dinovo stopped working with the new kernel in Feisty.

I upgraded from Edgy to Feisty Herd2 and at that time switched from KDE to Gnome.
First thought Gnome was causing the problem, but then found out KDE wasn't working either.

So restarted and selected the old kernel from Edgy (2.6.17-10-generic) and the keys are working again...

Should i report this in launchpad, and if so, where?


I've done the following test with the new kernel (linux-image-2.6.20-6-generic)


Running xev and pressing multimedia keys, but I don't see a thing (not a sign of a multimedia key which is pressed)

When I am at a real console and pressing multimedia keys nothing won't show up either.

And nor dmesg, nor syslog show any sign of a problem.

All other keys keep working fine.

---

### Post by pochu on 2007-02-04
You can file a bug here:
[https://launchpad.net/ubuntu/+source/hotkeys/+filebug](https://launchpad.net/ubuntu/+source/hotkeys/+filebug)

Regards
Pochu

---

### Post by lvanderree on 2007-02-05
Thanks

I installed the hotkeys package (I didn't had it installed in edgy), but this also didn't make any difference. 

Posted the bug under hotkeys, if this is wrong, I assume the maintainers know where to put it.

---

### Post by lvanderree on 2007-03-26
Just posting my bug is solved as from today (or yesterday)

I think because of an update (of the kernel to 2.6.20.13)

---

