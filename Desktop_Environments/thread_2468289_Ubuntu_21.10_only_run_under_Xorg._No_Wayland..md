---
title: "Ubuntu 21.10 only run under Xorg. No Wayland."
date: 2021-10-24
forum: Desktop Environments
---

### Post by jlalarcon on 2021-10-24
Hi All, Ubuntu mates.

After upgrade my system from 21.04 hirsute to 21.10 Impish, the desktop has loose the capability of run under the new graphic server Wayland. I run this on gnome-terminal:

$ echo $XDG_SESSION_TYPE 
x11
$

The output is the same no matter i choose both options present at the "gear" on the gdm3 login screen, "Ubuntu" or "Ubuntu on Xorg". This is part of my neofetch command output:

DE: GNOME 40.5
WM: Mutter
WM Theme: Adwaita
Theme: Yaru [GTK2/3]
Icons: Yaru [GTK2/3]
Terminal: gnome-terminal

Can you help me, please, mainly telling me where i must look for find a solution for this.

Thanks, very much, in advance.
Regards.

---

