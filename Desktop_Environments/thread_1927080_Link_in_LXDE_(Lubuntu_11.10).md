---
title: "Link in LXDE (Lubuntu 11.10)"
date: 2012-02-17
forum: Desktop Environments
---

### Post by Michele S on 2012-02-17
Hello, i made a script for a friend and I would put a link in his desktop for running it in a terminal window.

The script is named "aggiorna" and is located in /usr/bin/aggiorna with x permissions. It needs sudo to run properly.

The command to run the script is "sudo aggiorna".

I tried to make an aggiorna.desktop file in /usr/share/applications/ with this:

[Desktop Entry]
Name=Aggiorna il sistema
Exec=sudo aggiorna
Terminal=true
Type=Application
StartupNotify=false
Categories=Utility

But it doesn't work... i did something wrong? Can someone help me?

---

### Post by Michele S on 2012-02-17
I tried also Lxmed to create the link... the strange thing is that if I right click on the link and open "properties" that's what i get:

Name = Aggiorna il Sistema
Command = sudo aggiorna
Comment =

Execute in the terminal emulator (this is turned ON)

But when i try to open the link, it appears a terminal window that doesn't do anything at all (it doesn't take input and it doesn't give any output).

I also tried this way without succes:

Name = Aggiorna il Sistema
Command = sudo /usr/bin/aggiorna
Execute in the terminal emulator: ON

---

### Post by Michele S on 2012-02-18
I finally found a solution:

[Desktop Entry]
Name=Aggiorna il Sistema
Comment=
Icon=
Exec=lxterminal -e "sudo aggiorna"
Terminal=false

---

