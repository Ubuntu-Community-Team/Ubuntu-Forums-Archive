---
title: "Full screen terminal window auto run at log in, on desktop n.2"
date: 2013-01-13
forum: Desktop Environments
---

### Post by joepistone on 2013-01-13
Hi all. After a long time using KDE, I have switched to Unity. After few days, I'm appreciating simplicity and rationality at its base. I would like to do what the thread title suggests. In other words I would like that on desktop n.2, a gnome-terminal window runs automatically at login, in full screen mode.
Is It possible?

Thanks in advance.

---

### Post by Lila7714 on 2013-01-13
You could disable Gdm or lightdm to just start right up into terminal login. 
echo  "manual" | sudo tee -a /etc/init/lightdm.override

I think you could make a file /usr/share/xsessions/custom.desktop
[Desktop Entry] Name=gnometerm Exec=gnometerm

---

