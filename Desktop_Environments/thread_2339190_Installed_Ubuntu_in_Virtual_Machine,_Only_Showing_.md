---
title: "Installed Ubuntu in Virtual Machine, Only Showing Unity Launcher/Dock"
date: 2016-10-05
forum: Desktop Environments
---

### Post by jfblagdengmail.co on 2016-10-05
I installed Ubuntu in a Virtual Machine and then I installed Gnome3. It’s showing some Gnome3 stuff, but it’s also showing Ubuntu stuff, particularly the Unity Launcher. Here are the instructions I used: [https://websetnet.com/ubuntu-install-gnome-3-22-desktop-environment-ubuntu-16-04/](https://websetnet.com/ubuntu-install-gnome-3-22-desktop-environment-ubuntu-16-04/)

What went wrong? How do I make it more like Gnome3 and less like Unity? Why does Gnome only show up partially?

---

### Post by CantankRus on 2016-10-07
I don't see how you can get bits of both. They use different window managers.
What session are you in?
```
echo $DESKTOP_SESSION
```
Make sure you click on the cog wheel at the greeter and choose the "Gnome" session.

---

