---
title: "Problems with AIGLX/Beryl + NVidia-Twinview"
date: 2006-12-06
forum: Desktop Environments
---

### Post by gspazierer on 2006-12-06
I am using Ubuntu "nvidia-glx"-driver in Twinview-mode (NVidia 7600GS, 2x22" CRT) on Ubuntu/GNOME 6.10 Edgy and it works quite fine, but whenever I start beryl (installed from beryl-project.org-repository) my desktop freezes. I tried the latest NVidia-beta-driver using envy 0.72, but couldn't get Twinview to work. What can I do to run Beryl AND Twinview?

xorg.conf attached.


Best regards, Georg Spazierer

---

### Post by averagejoe84 on 2006-12-07
I'm not sure that is even able to work with duel displays my duel setup freaks out anytime I use anything with 3d acceleration.

---

### Post by RAOF on 2006-12-07
You should be able to.  You might want to add the --disable-glx-root-clipping option - **sudo nvidia-xconfig --disable-glx-root-clipping** should do that for you.

Maybe you should try Compiz?

---

### Post by averagejoe84 on 2006-12-07
glx-root-clipping option what does it do?

---

### Post by RAOF on 2006-12-08
As far as I can tell, it prevents: Clipping of GL drawing to just that which is in the root (as in, topmost, as in desktop) window.

It's nothing to do with the super-user or root-priviledges, if that's what you're worried about.

---

### Post by spd106 on 2006-12-10
Try looking in the Xorg.O.log file for clues.

I found that making sure xinerama was disabled helps. Add **Option "Xinerama" "False"** and **Option "NoTwinViewXineramaInfo" "False"** to the Device section.

It also removed the two "cubes" effect that I got from upgrading to beryl 0.1.2 (see attached).

---

