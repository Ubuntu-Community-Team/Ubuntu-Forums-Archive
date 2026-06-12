---
title: "Help i Broke xgl/compiz"
date: 2006-09-06
forum: Desktop Environments
---

### Post by caliel on 2006-09-06
after i installed the 686 kernel out of the repo it broke x (thats the name of the gui right?) when i tried "startx" it said somthing about missing screens or somthing so i opened  xorg.conf removed the changes i made to it when i set up xgl/compiz (if it matters i used the guide [here]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29") to install xgl/compiz) and i was able to start x but i want xgl back any one have any ideas to fix it? it whould be much appreciated

and does anyone know a good download manager that can pause and resume downloads?

---

### Post by armware on 2006-09-06
i did the same thing. you need to reinstall a few things such as the kernel headers, xorg and compiz. i wish i could give you a complete list, but i was just messing around assuming a reinstall was needed, but when i accidentally booted with the 686 kernel (i was going for the 386, as it was known working) everything was suddenly working. hope i helped.

---

