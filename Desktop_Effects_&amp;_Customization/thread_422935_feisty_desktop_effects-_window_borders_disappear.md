---
title: "feisty desktop effects- window borders disappear"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by r0ck80y on 2007-04-25
Hi.

After a fresh install of feisty ubuntu (gnome) and latest restricted drivers of nvidia (1.0.9631 through envy script), i launch the desktop effects from main menu..the effects in the menus, the   workspace cube etc work but the window borders on all windows disappear; so no wobbly effects :(

Whats happening??

---

### Post by stoppeltje on 2007-04-25
Add this "**Option "AddARGBGLXVisuals" "True"** to xorg.conf | section device

---

### Post by abhishek_laser on 2007-10-20
Thanks,works like a charm.but have to restart xorg before enabling desktop effects.

---

### Post by h3110w0r1d on 2007-11-07
I have the same problem, but how do I add the lines for it to work?

Thank You

---

