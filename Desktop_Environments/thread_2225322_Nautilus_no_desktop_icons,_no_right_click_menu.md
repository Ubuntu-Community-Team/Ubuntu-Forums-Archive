---
title: "Nautilus: no desktop icons, no right click menu"
date: 2014-05-20
forum: Desktop Environments
---

### Post by venkatramsam on 2014-05-20
I am running Ubuntu 12.04 with gnome desktop environment. After my last reboot, nautilus does not startup after login, there are no desktop icons, there is no right click menu. Even if I start nautilus from the terminal my problem is not solved. I tired setting the boolean show_desktop in gconf editor. Is there a way to get things back?

---

### Post by sethj3 on 2014-05-20
It seems like we are missing some context.. Did you set Nautilus to start when you login? It doesn't by default, so not sure why you're surprised by that. When you start Nautilus from the terminal, are there any errors? Where are you setting show_desktop?

---

### Post by venkatramsam on 2014-05-21
Starting nautilus from terminal just opens up my home folder. No visible errors on terminal. I could paste the output here it you want. I checked the parameters in gconf editor at applications/nautilus/preferences. The show_desktop boolean is ticked. What possibly can be the error causing my problem?

---

### Post by sethj3 on 2014-05-21
I'm not sure what the issue is at this point. If you could copy the terminal output it would be nice. I doubt it it important, but better check anyway ;)

What is the output of ```
gsettings get org.gnome.desktop.background show-desktop-icons
```?

Do you normally have to change that gconf key? Have you made any system changes lately? Installed anything new?

---

### Post by venkatramsam on 2014-05-21
false :)
gsettings set org.gnome.desktop.background show-desktop-icons true solved my issue 
Thanks :)

---

### Post by sethj3 on 2014-05-21
You're welcome. Might want to mark this solved then :-)

---

