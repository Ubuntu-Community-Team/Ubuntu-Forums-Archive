---
title: "GNOME Display Manager"
date: 2006-01-15
forum: General Help
---

### Post by ranatanveer on 2006-01-15
Could Someone help me i want to change in my GNOME display manager on text mode....
what command should i issue for that as a root user
because i want to adjust my gnome display setting...
my screen become blank as i installed ubuntu 
regards

Rana Tanveer

---

### Post by jasmuz on 2006-01-15
Maybe you are looking to reconfigure the X.Org server...

sudo dpkg --reconfigure xserver-xorg

---

### Post by aysiu on 2006-01-15
[QUOTE=jasmuz]
sudo dpkg --reconfigure xserver-xorg[/QUOTE] I thought the command was ```
sudo dpkg-reconfigure xserver-xorg
```

---

