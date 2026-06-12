---
title: "Set Gnome as Default In Natty Narwhal"
date: 2011-04-19
forum: Desktop Environments
---

### Post by powerofpi on 2011-04-19
This may sound like a silly question, but I can't seem to find the answer. How can I go about making Gnome the default desktop session in Natty?

---

### Post by Krytarik on 2011-04-19
You can change the system's default session option by "System -> Administration -> Login Screen" or the corresponding path in Unity. The settings will eventually be stored in "/etc/gdm/custom.conf", like this:
```
[daemon]
TimedLoginEnable=true
AutomaticLoginEnable=false
TimedLogin=krytarik
AutomaticLogin=krytarik
TimedLoginDelay=10
**DefaultSession=**[COLOR=Blue]**gnome**[/COLOR]
```Greetings.

Note: That name refers to the name of the respective *.desktop file in "/usr/share/xsessions". So, you have to check that if you want to set it manually.

---

