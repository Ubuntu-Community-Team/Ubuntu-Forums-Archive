---
title: "Desktop icon permissions"
date: 2006-06-24
forum: Desktop Environments
---

### Post by canadianwriterman on 2006-06-24
I'ce installed a desktop icon to run Sane, which needs to be run as root. How can I change the permissions on the icon to run as a user? Thanks.

---

### Post by aysiu on 2006-06-24
Well, it's not really an icon issue--it's a command issue. The command to run Sane needs to be run as root?

---

### Post by canadianwriterman on 2006-06-25
Yes, Sane needs to be run as root. So, in the desktop icon's properties, I've entered **sudo xscanimage** as the command line. Clicking on the icon now brings up a terminal window with a password prompt. When I enter my password, the terminal window closes and nothing happens. When I run xscanimage in the terminal only, Sane opens fine. I'd just like the convenience of being able to run it from an ison or, at least, a menu item.

---

### Post by NESFreak on 2006-06-25
you should use gksudo, this gives you a grafical interface where you can ener your password. sudo is for the commandline.

---

### Post by canadianwriterman on 2006-06-25
Well, gksudo does give me a graphical password box, however Sane still will not launch. The command line is now gksudo xscanimage. In terminal mode, xscanimage opens Sane. Anyone have any ideas?

EDIT: Okay, I feel dumb. The scanner has to be turned on before Sane will open. Works fine now. Duh.

---

### Post by raptros-v76 on 2006-06-25
make sure that the only thing in the launcher is gksudo xscanimage

---

### Post by raptros-v76 on 2006-06-25
also make sure that the "run in terminal" box is NOT checked

---

