---
title: "nautilus &lt;root&gt;"
date: 2006-01-31
forum: Desktop Environments
---

### Post by ESPOiG on 2006-01-31
k im runnin nautilus as the root user <gksudo nautilus> but in it all the icons are this little pixleated blank document sortof lookin one and the quick switch or wateva buttons that can take u bak to home etc r huge... y is this just cuz i chnaged my icons the roots ones r stuffd

and i cant login to my root account cuz even though it is enabled to be able to login on the logon screen it doesnt allow me at all

---

### Post by aysiu on 2006-01-31
Have you tried ```
gksudo gnome-theme-manager
```?

---

### Post by ESPOiG on 2006-01-31
it just says missing command to run ???

---

### Post by aysiu on 2006-01-31
[QUOTE=ESPOiG]it just says missing command to run ???[/QUOTE] That's not what I'm getting.

---

### Post by ESPOiG on 2006-01-31
well that is wat i get so what now does that mean that my root's theme manager is missin or culd it have sumtin to do with me not bein able to login as a root user

---

### Post by aysiu on 2006-01-31
Are you able to run just plain old ```
gnome-theme-manager
``` without the *gksudo* in front of it?

---

### Post by ESPOiG on 2006-01-31
dont worry my mistake i didnt put in gnome-theme-manager i just put in theme-manager

but it still didnt change the appearance of nautilus :S

---

### Post by ESPOiG on 2006-01-31
this is wat it looks like

---

### Post by manicka on 2006-01-31
You need to copy the specific theme's folder from ~/.themes to /usr/share/themes. Reapply the theme and you should be in business

---

### Post by ESPOiG on 2006-01-31
didnt work i copied my .themes into the user/share/themes folder *i think thats right and it didnt work even after a reboot :(

---

### Post by mcduck on 2006-01-31
icons aren't in the .themes directory, they are in .icons.

I solved this by creating links from my .themes and .icons to same folders in /root. Now root always has same theme and icons that I use :D

---

