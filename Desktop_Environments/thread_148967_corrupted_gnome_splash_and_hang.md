---
title: "corrupted gnome splash and hang"
date: 2006-03-23
forum: Desktop Environments
---

### Post by Ev.Eli on 2006-03-23
Hi all! I just came over here from the Gentoo camp, mainly because Gentoo is a little impracticle to maintain. Anyway, I just installed Breezy into one of my rigs. Install was smooth, but when I attempt to log in, I get a corrupted GNOME splash screen and the system hangs. I can open the Session dialog in GDM, but selecting any of the radio buttons causes similar corruption in that dialog and a hang. When the system hangs, I can still move the mouse, but I cannot switch to ttys and ctrl+alt+del have no effect.
My specs just in case they matter:
Athlon 64 3700 (may not be related, so I did not choose the AMD64 forum)
Geforce 7800GT graphics (PCI-e, obviousely)
nForce4 mobo
250GB SATA II HD
It would be nice if someone could shed some light on this issue.

---

### Post by ranf on 2006-03-24
This PCI-e graphics card is rather new, isn't it?

Can you boot in recovery mode? An `lspci' output might help a bit.

Do you use the i386 version?

---

