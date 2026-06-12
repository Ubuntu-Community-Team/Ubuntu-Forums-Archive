---
title: "Startup Problem with AMD-Duron 850"
date: 2006-01-17
forum: General Help
---

### Post by coolworld on 2006-01-17
Hi, hope somebody here can help me with my problem.

I'm installing Ubuntu 5.10 in a AMD Duron 850, the installation is successful without any problem, the problem starts when Ubuntu start after installation, it display the startup screen with the files being loaded but after that my screen went completely black and went to stand-by mode?

What happen and how do I solve this?

---

### Post by dcstar on 2006-01-17
[QUOTE=coolworld]Hi, hope somebody here can help me with my problem.

I'm installing Ubuntu 5.10 in a AMD Duron 850, the installation is successful without any problem, the problem starts when Ubuntu start after installation, it display the startup screen with the files being loaded but after that my screen went completely black and went to stand-by mode?

What happen and how do I solve this?[/QUOTE]
If your X settings aren't right, then:

CTRL-ALT-F1, you should get a text login screen. Login with your username, then:

sudo dpkg-reconfigure xserver-xorg

and select a specific resolution and refresh rate that your monitor is capable of displaying.

---

### Post by coolworld on 2006-01-18
Hey, thanks for the reply.

Will do the procedure that you post.

Thanks for the fast response.

---

