---
title: "Please Help"
date: 2006-08-13
forum: Desktop Environments
---

### Post by SilentJ on 2006-08-13
Please help, I was playing with trying to install xgl today and it crashed X. When I reboot I get this error message saying..
X window system version 7.0.0 ect...
then it says :
==log file /var/log/Xorg.o.log

and 
== useing file /etc/x11/xorg.conf

X server disabled Restart GDM when fixed or something. 

Anyhow, I installed xgl with the irections in the forums and it made my graphics all wack so i un-installed it and backtracked changing all the things back to the way they were before but now I cant do anything I dont get gnome at all just that message and the CLI. Is there any way to re-install Gnome or X or whatever so I dont have to completely re-install Ubuntu (Daper) I have so much stuff on there it would kill me to have to re-install.
please help!

thank you

---

### Post by bodyguard on 2006-08-13
If you have Nvidia video card make sure that your file /etc/gdm/gdm.conf-custom looks exactly like this:

```

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]

```

---

### Post by Greycloak on 2006-08-13
If you have an ATI card, check /etc/gdm/gdm.conf and look for

```
#0=Standard
1=Standard
```

change it to:

```
0=Standard
#1=Standard
```

---

