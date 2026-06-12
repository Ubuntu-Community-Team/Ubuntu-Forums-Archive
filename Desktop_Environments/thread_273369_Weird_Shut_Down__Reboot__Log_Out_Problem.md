---
title: "Weird Shut Down / Reboot / Log Out Problem"
date: 2006-10-07
forum: Desktop Environments
---

### Post by quickq111 on 2006-10-07
After Edgy was disastrous on my computer, today I clean installed Dapper. Everything works perfectly, except for one issue: whenever I log out, reboot, or shut down my computer (as well as refreshing Gnome), the entire screen just turns black with lines going through it, and the logging out / shutting down sound just freezes and an annoying buzzing sound is made.

However, starting up the machine is fine. 

I think it may have to do with the nVidia driver I installed, but I'm not sure. Is this a common problem? 

Please help,
Thanks.

---

### Post by quickq111 on 2006-10-08
Never mind, the problem was my nVidia FX5900 card with the driver...

Basically I had to disable graphical log out and shut down, but all is well.

---

### Post by prophet on 2006-10-08
How did you disable the graphical log out? Have the same problem but only when I reboot; Logout and shutdown is fine.

---

### Post by jstaple on 2006-10-10
How to remove shutdown reboot option in gnome login menu and desktop

In Gnome goto
1. Administration->Login window
2. Take the tick out of show actions menu.

This can also be done via config file /etc/gdm/gdm.conf if you like pain.

Please note I am a fellow traveler and by no means a expert.

J

](*,)

---

### Post by zek725 on 2006-10-31
I have a related shutdown problem since Edgy. Edgy Eft shutdown does not work. Freezes at WILL NOW HALT. Reboot works fine. I've reinstalled Edgy Eft from scratch and this happens. Dapper -> Edgy, it works fine.

---

