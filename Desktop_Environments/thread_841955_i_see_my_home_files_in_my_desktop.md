---
title: "i see my home files in my desktop"
date: 2008-06-26
forum: Desktop Environments
---

### Post by CGH on 2008-06-26
Hi,

this monday a upgrade from ubuntu 7.10 to 8.04, meanwhile i did that, i erase the folder "Escritorio" (i used to have "Desktop" and "Escritorio" (escritorio=desktop in english)) and keeping Desktop, now, after reboot i found that in my desktop i see me Home files, but not those in "Desktop", a firend told me to get back from the trash the folder Escritorio in Home, he said that's the problem, i tried, but i still keep seen my home files in the desktop, when i use nautilus, it has in the left menu the direct access to Escritorio, but it just keep sending me to my home

does anyone knows what happened and how to fix it?

note: this happens in gnome and kde

Greetings!

---

### Post by CGH on 2008-06-26
hi again,

i solved it:

i edit the file /home/israel/.config/user-dirs.dirs

i used to had this line

XDG_DESKTOP_DIR="$HOME/"

and i changed it for

XDG_DESKTOP_DIR="$HOME/Desktop"

restart the session and done

thanks to google!*

Greetings!

*the hard part was to fin the right question, the answer was the easy one

---

