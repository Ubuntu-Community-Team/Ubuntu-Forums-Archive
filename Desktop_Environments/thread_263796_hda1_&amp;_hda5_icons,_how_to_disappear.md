---
title: "hda1 &amp; hda5 icons, how to disappear?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by ::Lagro on 2006-09-23
I don't want icons of windows partitions on my desktop (hda1, hda5), but I want to have access at them.
How can I find a solution to this problem?

Thank you!

---

### Post by Omnios on 2006-09-23
Hi here is a fix

 Menu         :: Aplications / System Tools / Configuration editor //
config editor:: apps / nautilus / Desktop //

 Now on the right there will be a hole bunch of options which should have a checkbox for you mounts to remove them from the desktop and also show volumes which I think takes all of them off the desktop.

---

### Post by meng on 2006-09-23
Launch configuration editor (probably under Applications > System Tools)
Go apps > nautilus > desktop
Uncheck volumes_visible.

---

### Post by Average Joe on 2006-09-23
Don't mount them under /media, but somewhere else. Then they don't show up on your desktop anymore. Meng's solution also works, but if you then plugin a usb stick, it doesn't show up on your desktop either.

---

### Post by ::Lagro on 2006-09-23
Thank you for help!
I was it trough.

---

